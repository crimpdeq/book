# Crimpdeq

<p style="text-align:center;"><img src="assets/logo.png" width="40%"></p>

Meet Crimpdeq, a portable digital force sensor designed for climbers, coaches, and therapists to measure and train finger strength, pulling power, and endurance. It was inspired by [Tindeq Progressor](https://tindeq.com/product/progressor/), and works with the [Tindeq](https://tindeq.com/) and [Frez](https://www.frez.app/) apps.

## Specs

- Rechargeable battery with USB‑C charging
- Communicates via Bluetooth Low Energy (BLE)
- Open-source firmware written in Rust
- Open-source PCB design
- Automatic sleep when inactive
- Compatible with Tindeq Progressor app ([Android](https://play.google.com/store/apps/details?id=com.progressor&hl=es_419) | [iOS](https://apps.apple.com/es/app/tindeq-progressor/id1380412428))
- Compatible with Frez app (formerly ClimbHarder) ([Android](https://play.google.com/store/apps/details?id=com.holdtight.climbharder&pcampaignid=web_share) | [iOS](https://apps.apple.com/us/app/climbharder-no-hang-training/id6730120024))
- Sampling frequency: 80 Hz
- Design load: 1500 N (≈150 kg), full scale
- Precision:
    - 0.05 kg between 0 and 99 kg
    - 0.1 kg between 100 and 150 kg
- Operating temperature: 0–40 °C
- Dimensions: 80 × 90 × 35 mm
- Uses the [Tindeq Progressor API](https://tindeq.com/progressor_api/)

> ⚠️ **Warning**: Some of these specs come from the crane scale, if you use a different one, those values might change.

## Content of the Book

This book covers everything from assembly and calibration to firmware internals and PCB design. Below are the available sections:

- [Introduction](./introduction.md)
- [Making your own Crimpdeq](./assembly.md)
- [Calibration](./calibration.md)
- [Charging the Battery](./battery.md)
- [Firmware](./firmware.md)
- [PCB](./pcb.md)

> ⚠️ **Note**: If you're interested in reproducing this project or giving it a try, please, reach out! You can contact me via email (sergio.gasquez@gmail.com), [X (formerly Twitter)](https://x.com/Sergio_Gasquez) or [Bluesky](https://bsky.app/profile/sergiogasquez.bsky.social).
