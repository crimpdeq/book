# Crimpdeq

Meet Crimpdeq, an open‑source force guauge like [Tindeq Progressor](https://tindeq.com/product/progressor/), that works with the [Tindeq](https://tindeq.com/) and [Frez](https://www.frez.app/) apps.

The project relies on an ESP32‑C3 and uses an HX711 to get measurements from the crane scale. For more details, see the [Firmware](./firmware.md) chapter.

The PCB is finished but has not been manufactured yet; therefore it’s untested.

## Specs

- Sampling Frequency: 80 Hz
- Design Load: 1500 N (150 kg) (Full Scale)
- Precision:
    - *0.05 kg* between 0 and 99 kg
    - *0.1 kg* between 100 kg and above
- Working temperature: 0ºC - 40ºC
- Dimension: 80 mm x 90 mm x 35 mm
- USB-C rechargeable battery

> ⚠️ **Note**:  Some of these specs come from the crane scale, if you use a different one, those values might change.
