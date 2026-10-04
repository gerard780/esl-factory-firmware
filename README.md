# ESL factory firmware dumps

Unaltered factory/stock full-flash captures from electronic shelf label (ESL)
tags. Each binary preserves the complete captured flash address range.

## Available captures

| Tag | Capture date | Size | Verification | Download |
| --- | --- | --- | --- | --- |
| Hanshow Nebular Pro-154Q-N, C3HW2 | 2026-10-03 | 512 KiB | Two full reads match byte for byte; initial samples and remote/local hashes match | [Factory dump](dumps/hanshow/nebular-pro-154q-n/factory-2026-10-03.bin) |
| Hanshow Nebular Pro 266, reference specimen | 2026-09-28 | 512 KiB | One full read; initial sample, ten fresh 256-byte reads, and remote/local hashes match | [Factory dump](dumps/hanshow/nebular-pro-266/factory-2026-09-28.bin) |

Both images cover `0x000000` through `0x07ffff` inclusive and were captured
through SWS. The flash JEDEC ID was `eb6013` for both specimens. No flash
programming, erase, or unlock commands were issued during either capture.

## Provenance

Factory state was reported by the owner. Readback checks establish capture
consistency; OEM origin has not been independently authenticated. The 266
reference specimen was identified by matching its printed label identifiers
to records in the saved flash. Its exact case revision and PCB marking were
not recorded, so these are left unspecified.

The 154Q-N specimen has PCB `HSEL4Q_01_54M_39` and MCU marking `MS9100 B410A`.
Capture details and SHA-256 values are recorded in [manifest.json](manifest.json).

Full-flash snapshots retain original per-device identifiers, calibration,
configuration, and runtime data. Cross-device restoration has not been validated.

## Verify downloads

Run from the repository root:

```sh
sha256sum -c SHA256SUMS
```

The files are preserved byte for byte without redaction or modification.
Original OEM firmware remains attributed to its respective rights holders;
this repository grants no license to that firmware.
