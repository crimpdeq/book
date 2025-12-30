# Firmware

The firmware is written in async Rust (`no_std`) using [`esp-hal`](https://github.com/esp-rs/esp-hal) and a small set of supporting crates.

## Prerequisites

To build and upload the firmware to your device, ensure you have the following installed:
- [Rust](https://rustup.rs/)
- The `stable` toolchain with the ESP32-C3 target architecture installed:
  ```bash
  rustup toolchain install stable --component rust-src --target riscv32imc-unknown-none-elf
  ```
- [`probe-rs`](https://probe.rs/), see [installation instructions](https://probe.rs/docs/getting-started/installation/)
  - OS notes:
    - Linux: set up udev rules for your debug probe or USB‑Serial device (see [`probe-rs` udev guide](https://probe.rs/docs/getting-started/installation/#udev-rules)).
    - Windows/macOS: ensure the correct USB drivers are installed and select the appropriate serial port in your tooling.

## How to Build the Firmware
To build the firmware, run:
```bash
cargo build --release
```

This compiles the firmware only. To build and flash the device, see [Build and Flash your Device](#build-and-flash-your-device).

## How to Flash Your Crimpdeq

### Erase Device Memory
If this board was previously used for other projects, erase its flash once:
```bash
probe-rs erase
```

> ⚠️ **Note**:  Erasing is only needed once. Avoid erasing routinely, or you will lose your [calibration values](./calibration.md).

### Build and Flash Your Device
With a [custom runner](https://doc.rust-lang.org/cargo/reference/config.html#targettriplerunner) configured in `.cargo/config.toml`, you can build, flash, and open a serial monitor with:
```bash
cargo run --release
```
This opens a serial monitor, allowing you to view log messages in real time.

To modify the [log level](https://defmt.ferrous-systems.com/filtering), update the `DEFMT_LOG` value in `.cargo/config.toml` or set it when running the command:
```bash
DEFMT_LOG=debug cargo run --release
```

> ⚠️ **Note**: If your DevKit does not include USB‑Serial‑JTAG, flash via UART by updating the custom runner in `.cargo/config.toml` to use [`espflash`](https://github.com/esp-rs/espflash/tree/main/espflash#cargo-runner) instead of `probe-rs`.

### Configuring Environment Variables

If you need to change `DEVICE_ID`, `DEVICE_NAME`, or `DEVICE_VERSION_NUMBER`, update their values in [`.cargo/config.toml`](https://github.com/crimpdeq/crimpdeq-firmware/blob/main/.cargo/config.toml).

After making changes, rebuild and flash the device for the new values to take effect.

## Code Structure

### `hx711`
This module implements the load cell functionality. It's an `async` version of the [loadcell](https://crates.io/crates/loadcell) crate with additional modifications.

### `ble`
This module implements the Bluetooth Low Energy (BLE) functionality:
- Defines the GATT server and services
- Handles advertising and connections
- Defines the Progressor service with data point and control point characteristics

### `progressor`
The `progressor` module implements the [Tindeq API](https://tindeq.com/progressor_api/), enabling BLE (Bluetooth Low Energy) communication between the ESP32-C3 and a smartphone.

### Main Tasks
The `main.rs` file defines several asynchronous tasks that run concurrently:
- `measurement_task`:
  - Initializes the load cell.
  - Handles taring and reads measurements from the sensor.
- `ble_task`:
  - Long‑running background task required alongside other BLE tasks.
- `gatt_events_task`:
  - Processes GATT events such as control‑point writes.
- `data_processing_task`:
  - Handles sending notifications with data points.
- `battery_voltage_task`:
  - Periodically reads the battery voltage.
- `deep_sleep_task`:
  - Monitors inactivity; after a timeout, the device enters deep sleep.

Communication between tasks occurs via a [`Channel`](https://docs.embassy.dev/embassy-sync/git/default/channel/struct.Channel.html).
