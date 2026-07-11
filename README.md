<p align="center">
  <img src="banner.jpg" alt="Disable AVB Banner" width="100%" />
</p>

<h1 align="center">🛡️ Disable AVB (Android Verified Boot) Flashable Installer 🛡️</h1>

<p align="center">
  <strong>A recovery-flashable POSIX installer package to query, disable, and bypass Android Verified Boot (AVB 2.0) verity and verification flags.</strong>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="License: MIT" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Platform-Android%20Recovery-orange.svg?style=for-the-badge" alt="Target Platform" /></a>
  <a href="#"><img src="https://img.shields.io/badge/Architecture-ARM64-blue.svg?style=for-the-badge" alt="Target CPU" /></a>
</p>

---

> [!CAUTION]
> **I AM NOT RESPONSIBLE FOR BRICKED DEVICES.** Flashing partition verification bypasses and AVB-disable installers carries a significant risk of bricking your device or causing boot-loops. You are solely responsible for any damage or data loss. Proceed at your own risk.

## 📖 Introduction

This repository contains a streamlined, POSIX-compliant **AVB Vbmeta Disabler** flashable package designed to run natively inside custom recovery environments (TWRP, OrangeFox, PBRP). 

It utilizes the `avbctl` engine to disable dm-verity and partition verification. This prevents boot-loops, verification warnings, and mounting lockups when running modified partitions or custom system ROM ports.

---

## ⚡ Key Improvements

The original installer script contained structural bugs that caused failures on modern devices. I refactored the codebase to incorporate the following fixes:

1.  🛠️ **RAM-Buffered Execution (`/tmp/` Workspace)**:
    *   *The Bug*: The original updater script attempted to extract `avbctl` to `/system/bin/`. On Android 10+ devices with dynamic logical partitions, `/system` is unmounted or mounted read-only in recovery mode, causing the installation to crash with write-permission errors.
    *   *The Fix*: Refactored to extract `avbctl` into `/tmp/` (RAM-disk workspace), allowing error-free extraction and execution on all systems.
2.  🧹 **In-Process Cleanup**:
    *   Natively removes the `avbctl` binaries from the temporary workspace at the end of the script, leaving zero footprint.
3.  📝 **Clean Log Outputs**:
    *   Reformatted the status logging and warnings to be clean and developer-compliant.

---

## 🚀 How to Install

1.  Download the compiled installer package:
    *   [**Disable-Vbmeta-Flashable.zip**](https://github.com/mehraann19/Disable-Vbmeta-Flashable/releases/download/v1.0.0/Disable-Vbmeta-Flashable.zip)
2.  Boot your device into custom recovery (TWRP/OrangeFox).
3.  Go to **Install** and select the ZIP package.
4.  Swipe to flash.
5.  Reboot the device.

> [!WARNING]
> If your device stays stuck in recovery mode or boot-loops after disabling AVB, you may need to perform a **Format Data** operation inside your recovery settings.

---

## 👥 Credits

*   **Logic & Patch Refactoring**: **Mehraan** (GitHub: [mehraann19](https://github.com/mehraann19))
*   **Original Script Structure**: Community release developers

---

## 📄 License

This installer package is licensed under the [MIT License](LICENSE) - see the file for details.
All binary utilities and recovery parameters belong to their respective copyright holders.
