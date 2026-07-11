# 🛡️ Disable AVB (Android Verified Boot) Flashable Installer v1.0.0

A recovery-flashable POSIX updater ZIP to query, disable, and bypass Android Verified Boot (AVB 2.0) verity and verification flags.

### 🛠️ Refactoring & Bug Fixes
* **RAM-Buffered Execution (/tmp/)**: Fixed structural errors in the original installer package where it attempted to unzip `avbctl` to the `/system/bin` path. Under modern dynamic logical partition setups, `/system` is read-only and unmounted in custom recovery, causing write-permission errors. The script now unzips and runs `avbctl` safely inside `/tmp` (RAM-disk workspace) and performs a clean footprint deletion at the end of the flashing loop.
* **Professionalized Messages**: Removed raw informal slang and standardized logging indicators.

---

### 🚀 Flashing Instructions
1. Boot into custom recovery (TWRP/OrangeFox/PBRP).
2. Go to **Install**, select **`Disable-Vbmeta-Flashable.zip`**, and swipe to flash.
3. Reboot device.

> [!WARNING]
> If your device reboots into recovery or stays stuck on boot, perform a **Format Data** operation inside your recovery settings.
