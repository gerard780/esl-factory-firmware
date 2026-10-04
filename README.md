# ESL factory firmware dumps

Unaltered factory/stock full-flash captures from electronic shelf label (ESL)
tags. Each binary preserves the complete captured flash address range.

## Available captures

| Tag | Capture date | Native resolution | Size | Download |
| --- | --- | --- | --- | --- |
| Hanshow Nebular Pro-154Q-N, C3HW2 | 2026-10-03 | 200 × 200 | 512 KiB | [Factory dump](dumps/hanshow/nebular-pro-154q-n/factory-2026-10-03.bin) |
| Hanshow Nebular Pro-266Q-N, E3LW2 | 2026-09-28 | 152 × 296 | 512 KiB | [Factory dump](dumps/hanshow/nebular-pro-266/factory-2026-09-28.bin) |

Both images cover `0x000000` through `0x07ffff` inclusive and were captured
through SWS. The flash JEDEC ID was `eb6013` for both specimens. No flash
programming, erase, or unlock commands were issued during either capture.

## Capture verification

- **154Q-N:** two independent 524,288-byte reads match byte for byte. Initial
  4 KiB samples and remote/local SHA-256 hashes match; no transport faults were
  recorded.
- **266Q-N:** one 524,288-byte read, checked against the initial sample and ten
  fresh 256-byte reads across flash. Remote/local SHA-256 hashes match. On
  2026-09-29, before installing replacement firmware, a further 79,872-byte
  partial read and 38 independently read 256-byte samples matched this capture.
  A second complete factory read was not performed.

## Provenance

Factory state was reported by the owner. Readback checks establish capture
consistency; OEM origin has not been independently authenticated. Both captures
have stored identifiers that match the corresponding photographed printed
barcodes:

| Capture | Printed barcode | Stored four-byte identifier |
| --- | --- | --- |
| 154Q-N | `514583053996242823` | `EE31D387` |
| 266Q-N reference | `343581053587707526` | `D5D81286` |

The 154Q-N capture records identify case revision `C3HW2`, PCB
`HSEL4Q_01_54M_39`, MCU marking `MS9100 B410A`, and FCC ID `2BPF3-NP1540`.
The supplied photos confirm these hardware markings.

The 266Q-N specimen photos document case marking `404545`, revision `E3LW2`,
FCC ID `2BPF3-NP2660`, PCB `HSEL7_02_66M_30`, and MCU marking `MS9100 B410A`.
Both photographed case labels state that the tags were made in Vietnam.

Capture details and SHA-256 values are recorded in [manifest.json](manifest.json).

Full-flash snapshots retain original per-device identifiers, calibration,
configuration, and runtime data. Cross-device restoration has not been validated.

## Hardware reference photos

Owner-supplied photos, cropped directly from the original JPEGs and saved as
lossless PNGs. Lettering and circuit details are preserved without retouching.
Each specimen's photos are stored in the same folder as its firmware dump.

| Photo | Visible markings | Cropped reference |
| --- | --- | --- |
| 1 | `Nebular Pro-154Q-N`, `450546`, `C3HW2`, `2BPF3-NP1540`; made in Vietnam | [Model and case label](dumps/hanshow/nebular-pro-154q-n/photo-01-154q-n-label.png) |
| 2 | Flex `60105-01225`, `1.5HR_V1.0`, `2024-11-13`; pads `NRST`, `GND` | [Panel flex and rear board](dumps/hanshow/nebular-pro-154q-n/photo-02-panel-flex.png) |
| 3 | PCB `HSEL4Q_01_54M_39`, `24-08`; MCU `MS9100 B410A`; Hanshow `65 mAh`, `3.0 V` battery | [154 board and battery](dumps/hanshow/nebular-pro-154q-n/photo-03-154-board-battery.png) |
| 4 | MCU `MS9100 B410A`; pads `RST`, `TX`, `RX`, `SWS`, `VCC`, `GND` | [MCU and programming pads](dumps/hanshow/nebular-pro-266/photo-04-mcu-test-pads.png) |
| 5 | PCB `HSEL7_02_66M_30`; panel signals including `DC`, `CS`, `RST`, `BUSY` | [266 panel board](dumps/hanshow/nebular-pro-266/photo-05-266-panel-board.png) |
| 6 | `Nebular Pro-266Q-N`, `404545`, `E3LW2`, `2BPF3-NP2660`; made in Vietnam | [266 model and case label](dumps/hanshow/nebular-pro-266/photo-06-266q-n-label.png) |

## Verify downloads

Run from the repository root:

```sh
sha256sum -c SHA256SUMS
```

The files are preserved byte for byte without redaction or modification.
Original OEM firmware remains attributed to its respective rights holders;
this repository grants no license to that firmware.
