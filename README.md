# 💻 Dell Inspiron 14 5425 Hackintosh (AMD Ryzen 5 5625U)

This repository provides a highly optimized and stable EFI for running **macOS Tahoe (26.3.2)** on the Dell Inspiron 14 5425 with AMD Ryzen "Barcelo" architecture. This build achieves near-perfect MacBook Pro functionality.


## 🌟 Overview
After extensive testing with various audio configurations (including VoodooHDA patches and node analysis), this setup achieves stable GPU acceleration and high-quality internal stereo microphone support, making it a daily-driver ready Hackintosh.

## 💻 Hardware Specifications
- **Model:** Dell Inspiron 14 5425
- **CPU:** AMD Ryzen 5 5625U (6C/12T)
- **iGPU:** AMD Radeon™ Graphics (**2GB VRAM spoofed via UMAF**)
- **RAM:** (Your RAM size, e.g., 16GB) DDR4
- **Audio:** Realtek ALC3254 & AMD ACP Digital Mic
- **Wi-Fi/BT:** Intel® Wi-Fi 6E AX210
- **Display:** 14" FHD+ (1920 x 1200)

## ✅ What's Working
- **GPU Acceleration:** Full Metal support with 2GB VRAM for smooth UI.
- **Display Outputs:** - USB-C DisplayPort (Up to 4K @ 60Hz)
  - HDMI (Up to 4K @ 60Hz)
- **Audio:** Internal Speakers & Headphone Jack (Auto-switching via VoodooHDA).
- **Microphone:** **Internal Digital Microphone (AMD ACP)** - Crystal clear stereo sound.
- **Power Management:** Sleep / Wake, Battery Status, and USB-C PD Charging.
- **Input:** Precision Trackpad, Backlit Keyboard, and all USB 3.1 ports.
- **Wireless:** Wi-Fi 6E & Bluetooth (Intel AX210).

## ❌ Not Working / Known Issues
- **Headset Microphone:** Only the internal digital mic is currently supported for input. External 3.5mm combo jack mics are recognized as line-in but may not pick up sound.

## 📦 Required External Drivers (Kexts)
To keep the EFI lightweight, some kexts must be downloaded or installed manually.

### 📶 Wi-Fi & Bluetooth
Download the latest drivers for Intel AX210 from the official site:
- **Official Link:** [OpenIntelWireless](https://openintelwireless.github.io/)
- Add them to `OC/Kexts` and update your `config.plist`.

### 🎙️ Internal Microphone (AMD ACP)
To enable the high-quality internal microphone, install the driver to your system:
1. Copy `AMDMicrophone.kext` to `/Library/Extensions/`.
2. Run these commands in Terminal:
   ```bash
   sudo chown -R root:wheel /Library/Extensions/AMDMicrophone.kext
   sudo chmod -R 755 /Library/Extensions/AMDMicrophone.kext
   sudo kmutil load -p /Library/Extensions/AMDMicrophone.kext
