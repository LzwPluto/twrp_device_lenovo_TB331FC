# TWRP Device Tree for Lenovo Xiaoxin Pad 2024 (`TB331FC` / `p255`)

* **SoC**: Qualcomm Snapdragon 685 4G (`SM6225-AD` / `bengal`)
* **Display**: 1200 x 1920 IPS LCD (Himax HX83102 + KTZ8866 backlight)
* **Touchscreen**: Novatek NT36523N (`nvt36523_spi.ko` + `novatek_ts_fw.bin` bundled)
* **Boot Architecture**: Android 14 / GKI 5.15, Boot Header v4, dedicated `recovery_a` / `recovery_b` (100 MiB, ramdisk-only `kernel_size=0`), Virtual A/B + 12 GiB `super`.

## Cloud Build via GitHub Actions

1. Push this repository to GitHub.
2. Open the **Actions** tab -> select **Build TWRP for Lenovo TB331FC** -> click **Run workflow**.
3. Wait ~15 minutes and download `TWRP-TB331FC-recovery` (`recovery.img`) from the Artifacts section.

## Flashing (Safe Slot B Test First)

```bash
# Flash to Slot B recovery first without touching Slot A
fastboot flash recovery_b recovery.img
# Or test directly if your slot A is active:
fastboot flash recovery_a recovery.img
fastboot reboot recovery
```

> **Note**: Stock `recovery.img` can always be restored via `fastboot flash recovery_a recovery.img`.
