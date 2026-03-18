# 💻 Dell Inspiron 14 5425 Hackintosh (AMD Ryzen 5 5625U)

## 🚀 CONFIRMED WORKING ON: **macOS Tahoe (26.3.2)** 🚀
This repository provides a highly optimized EFI for the Dell Inspiron 14 5425. It achieves near-perfect MacBook Pro functionality on the latest macOS architecture.


## 🌟 Overview
This build is a result of intensive tuning, including BIOS VRAM expansion and advanced audio node patching. It is one of the few repositories to achieve **stable GPU acceleration and high-quality stereo microphone support** on a Ryzen "Barcelo" laptop.

## 💻 Hardware Specifications
- **Model:** Dell Inspiron 14 5425
- **CPU:** AMD Ryzen 5 5625U (6C/12T)
- **iGPU:** AMD Radeon™ Graphics (**2GB VRAM via UMAF**)
- **Audio:** Realtek ALC3254 & AMD ACP Digital Mic
- **Wi-Fi/BT:** Intel® Wi-Fi 6E AX210
- **Display:** 14" FHD+ (1920 x 1200)

## ✅ What's Working
- **GPU Acceleration:** Full Metal support with 2GB VRAM.
- **Display Outputs:** USB-C DP & HDMI (Both 4K @ 60Hz).
- **Audio:** Internal Speakers & Headphone Jack (Auto-switching).
- **Microphone:** **Internal Digital Microphone (AMD ACP)** - Crystal clear stereo sound.
- **Power:** Sleep / Wake, Battery Status, and USB-C PD Charging.
- **Input:** Precision Trackpad, Backlit Keyboard.

## 📦 Required External Drivers (Kexts & Apps)

### 🔊 Audio (VoodooHDA)
To enable Speaker and Headphone output, you **MUST** install the VoodooHDA package:
1. Download and install **VoodooHDA.pkg**.
2. This is required for the Preference Pane and kernel-level audio management.

### 🎙️ Internal Microphone (AMD ACP)
Install the driver to your system:
1. Copy `AMDMicrophone.kext` to `/Library/Extensions/`.
2. Run these commands in Terminal:
   ```bash
   sudo chown -R root:wheel /Library/Extensions/AMDMicrophone.kext
   sudo chmod -R 755 /Library/Extensions/AMDMicrophone.kext
   sudo kmutil load -p /Library/Extensions/AMDMicrophone.kext
