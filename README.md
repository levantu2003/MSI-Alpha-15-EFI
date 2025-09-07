# MacOS on MSI Alpha 15-B5EEK - Ryzen 5 5600H & Radeon RX 6600M

OpenCore EFI for running macOS Sequoia 15.6.1 on MSI Alpha 15-B5EEK with AMD Ryzen 5 5600H and Radeon RX 6600M.

## Considerations

This EFI is provided for reference purposes only. I do not recommend using it without understanding the risks involved in Hackintosh setups. This setup is based on personal experience and may require adjustments for your specific hardware.

## Table of Contents

- [Specifications](#specifications)
- [What's Working](#whats-working)
- [What's not Working](#whats-not-working)
- [Bios Options](#bios-options)
- [Kexts Used](#kexts-used)
- [SSDTs Used](#ssdts-used)
- [Credits](#credits)
- [Installation](#installation)
- [Troubleshooting](#troubleshooting)

## Specifications

| Component | Details |
|-----------|---------|
| Model | MSI Alpha 15-B5EEK |
| BIOS Version | E158LAMS.10B |
| CPU | AMD Ryzen 5 5600H |
| dGPU | AMD Radeon RX 6600M 8GB |
| RAM | 32GB DDR4 3200MHz |
| NVMe | Lexar 1TB for macOS |
| WiFi | Intel AX210 |
| Ethernet | Realtek RTL8111 |
| Audio | Realtek ALC287 |
| LCD Panel | 15.6" FHD IPS 144Hz |
| OpenCore Version | 1.0.1 (DEV) |
| SMBIOS | MacBookPro16,3 |
| macOS Version | Sequoia 15.6.1 |

## What's Working

- ✅ CPU (AMD Vanilla Kernel Patches)
- ❌ dGPU (not used with NootedRed)
- ✅ Brightness Control (using Lunar app)
- ❌ HDMI A/V out (not working)
- ✅ USB (all ports working with USBMap)
- ✅ Keyboard (VoodooPS2Controller + Karabiner-Elements)
- ✅ Audio (AppleALC with layout-id 56)
- ✅ P2 Mic (working with AppleALC)
- ✅ Trackpad (VoodooI2C)
- ✅ Ethernet (RealtekRTL8111)
- ✅ Intel WiFi (AirportItlwm)
- ✅ Bluetooth (Intel AX210 with IntelBluetoothFirmware + BlueToolFixup)
- ✅ Battery (SMCBatteryManager)
- ✅ Apple TV+ DRM (with CFG_LINK_FIXED_MAP=1)
- ✅ iServices (iMessage/FaceTime tested)
- ✅ Shutdown/Reboot
- ✅ Sleep/Wake
- ✅ AirDrop (one-way, as reported)

## What's not Working

- ❌ Integrated iGPU display (only works through DP/HDMI as this laptop lacks MUX Switch)
- ❌ HDMI A/V out (not working)
- ❌ dGPU (not used with NootedRed)

## Bios Options

- Only Discrete GPU enabled
- Secure Boot Disabled

## Kexts Used

- AMDRyzenCPUPowerManagement.kext - Power management for AMD processors
- AMFIPass.kext - Bypasses AMFI for unsigned kexts
- AirportBrcmFixup.kext - Patches Broadcom WiFi
- AirportItlwm.kext - Intel WiFi driver
- AppleALC.kext - Native HD audio for ALC287
- AppleMCEReporterDisabler.kext - Disables AppleIntelMCEReporter
- BlueToolFixup.kext - Patches Bluetooth stack
- BrightnessKeys.kext - Brightness key support
- ECEnabler.kext - Embedded Controller access
- ForgedInvariant.kext - Bypasses GPU checks
- GenericUSBXHCI.kext - USB 3.0 support
- IntelBluetoothFirmware.kext - Intel Bluetooth firmware
- IntelBTPatcher.kext - Intel Bluetooth patcher
- IO80211FamilyLegacy.kext - Legacy WiFi family
- IOSkywalkFamily.kext - Skywalk networking
- itlwm.kext - Intel WiFi (alternative)
- Lilu.kext - Kext patching platform
- NootedRed.kext - AMD GPU support
- NVMeFix.kext - NVMe compatibility
- RealtekRTL8111.kext - Ethernet driver
- RestrictEvents.kext - Blocks unwanted processes
- SMCAMDProcessor.kext - AMD processor monitoring
- SMCBatteryManager.kext - Battery readings
- SMCLightSensor.kext - Light sensor support
- USBMap.kext - USB port mapping
- VirtualSMC.kext - SMC emulator
- VoodooI2C.kext & VoodooI2CHID.kext - Trackpad support
- VoodooPS2Controller.kext - Keyboard/mouse support

## SSDTs Used

- SSDT-ALS0.aml - Ambient Light Sensor
- SSDT-dGPU-Off.aml - Disable discrete GPU
- SSDT-PLUG-ALT.aml - CPU power management
- SSDT-PNLF.aml - Backlight control
- SSDT-USB-Reset.aml - USB reset
- SSDT-USBX.aml - USB power management
- SSDT-XOSI.aml - Spoof Windows for ACPI

## Credits

- [OC-Little-Translated](https://github.com/5T33Z0/OC-Little-Translated) for guides
- [AMD-OSX](https://forum.amd-osx.com/) community
- [its-ashu-otf](https://github.com/its-ashu-otf/MSI-Alpha-15-Hackintosh) for reference EFI
- [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) for OpenCore guides
- [Acidanthera](https://github.com/acidanthera) for OpenCore and kexts
- All contributors to Hackintosh community

## Installation

1. Download the EFI folder
2. Mount your EFI partition
3. Copy the EFI folder to EFI partition
4. Adjust config.plist if necessary (SMBIOS, boot-args)
5. Reboot and select the EFI in OpenCore picker

## Troubleshooting

- If WiFi doesn't work, try switching to itlwm
- If using AirportItlwm, use OpenCore Legacy Patcher (OCLP) to patch for full compatibility
- AirDrop one-way: This is a known limitation with Intel WiFi on macOS
- Update OpenCore and kexts regularly for Sequoia compatibility

**Note:** This EFI is for Sequoia 15.6.1. For other versions, you may need to update kexts and OpenCore.
