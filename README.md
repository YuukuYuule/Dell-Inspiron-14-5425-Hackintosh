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
- **Audio:** Internal Speakers & Headphone Jack (Auto-switching).(AppleALC)
- **Microphone:** **Internal Digital Microphone (AMD ACP) & Headphone Mic(Apple ALC)** -
- **Power:** Sleep / Wake, Battery Status, and USB-C PD Charging.
- **Input:** Precision Trackpad, Backlit Keyboard.

## Apple ALC
- alcid=33 **Working ComboJack**
- Need To install **Apple HDA.kext** on System/Library/Exstensions (**macOS Tahoe**)

## 📦 Required External Drivers (Kexts & Apps)

### 📶 Wi-Fi & Bluetooth (Intel AX210)
To keep the EFI folder lightweight, the wireless drivers are **NOT** included. Please download the latest versions from the official site:

1. **Official Link:** [OpenIntelWireless (itlwm)](https://openintelwireless.github.io/)
2. **Installation:**
   - Download **AirportItlwm.kext** (Match your macOS version: Sonoma/Sequoia/).
   - Download **IntelBluetoothFirmware.kext** & **IntelBTPatcher.kext**.
3. **Setup:**
   - Add these kexts to your `OC/Kexts` folder.
   - Update your `config.plist` to enable them.

### 🎙️ Internal Microphone (AMD ACP)
This build uses the excellent driver by **qhuyduong**. To enable high-quality internal stereo mic support:

1. **Credits:** [AMDMicrophone (qhuyduong)](https://github.com/qhuyduong/AMDMicrophone)
2. Copy `AMDMicrophone.kext` to `/Library/Extensions/`.
3. Run these commands in Terminal:
   ```bash
   sudo chown -R root:wheel /Library/Extensions/AMDMicrophone.kext
   sudo chmod -R 755 /Library/Extensions/AMDMicrophone.kext
   sudo kmutil load -p /Library/Extensions/AMDMicrophone.kext
   
### 🚀 Advanced Performance: VRAM Expansion (Essential!)
By default, the VRAM is limited to 512MB, which causes UI lag in macOS. I highly recommend increasing it to **2GB** using **Smokeless_UMAF**.

1. Download [Smokeless_UMAF](https://github.com/DavidS95/Smokeless_UMAF) and create a bootable USB.
2. Boot from the USB and navigate to:
   - **Device Manager** -> **AMD CBS** -> **NBIO Common Options** -> **GFX Configuration**
3. Change the following settings:
   - **Integrated Graphics Controller:** `Forces`
   - **UMA Mode:** `UMA_SPECIFIED`
   - **UMA Frame Buffer Size:** `2G`
4. Save and Exit. 
5. In macOS, you will see **2GB VRAM**, providing much smoother UI fluidity and Metal performance.
