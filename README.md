# Lenovo L480 OpenCore

This cheaply bought laptop beats the hell out of my Macbook 2016 (A1708) except for the screen quality/resolution and the poorer sound output, and lack of aluminium unibody. However the legendary Thinkpad keyboard is light-years ahead, and the nipple too is useful.  These laptops are going cheap, as is the later L580 which is more-or-less identical, so I'd recommend them, definitely. Thanks to everyone involved in OpenCore, the coders, the kext builders, and those who share their setups to help others.

Running Sonoma 14.5 presently, but also worked with Monterey and Ventura previously. The config.plist needs an SMBIOS of MacBookPro 15.

## Hardware

- Intel Core i5 8350
- 2 x 16GB DDR4 2400
- Intel AX210NGW Wifi/Bluetooth    
- 1080P Screen (non-touch)

## Working

- Touchpad with multi-point and gestures
- Trackpoint nipple
- Internal Audio Speakers
- Internal Microphone
- Headphone jack output
- Webcam
- Internal 2280 NVME and 2240 NVME plugged into WAN port.
- Wifi/Bluetooth (was Intel 9265 NGW, now using AX210 NGW - no configuration changes necessary for either)
- In-built Ethernet
- Heat sensors for CPU, RAM, DISK
- Keyboard Backlight (requires YogaSMCPane installed, see blow)

## Not Working/Untested

- Sleep (needs `sudo pmset -a standby 0` to prevent trackpad failure after wake but often still doesn't work with extreme unresponsivness/slugishness)
- HDMI Output (untested)
- BayHub Tech Integrated Smart Card Reader not working

# Installing YogaSMCPane

This is required for the keyboard backlight to work and is obtained from [YogaSMC](https://github.com/zhen-zen/YogaSMC)

1. In Finder, copy YogaSMCPane.prefPane to /Library/PreferencePanes
2. Copy YogaSMCNC.app to /Applications
3. Open System Settings/Security
4. Start YogaSMCNC.app and choose 'Open Anyway' from Security in System Settings
5. In the Menu Toolbar for the app, choose 'Preferences' and repeat 'Open Anyway' as in the previous step.
6. You should see 'YogaSMCPane' in System Preferences now

# Kexts Used

## [Acidanthera (OpenCore Project)](https://github.com/acidanthera)

- [Lilu](https://github.com/acidanthera/Lilu) (Mandatory)
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC) (Required emulate Apple SMC)
- [WhateverGreen](https://github.com/acidanthera/WhateverGreen) (Required for the GPU except if using a non-Intel AMD APU)
- [RestrictEvents](https://github.com/acidanthera/RestrictEvents) - block unwanted processes causing compatibility issues
- [AppleALC](https://github.com/acidanthera/AppleALC) - for in-built audio
- [NVMEFix](https://github.com/acidanthera/NVMeFix) - (optional for fixing NVME issues)
  
  

## Wireless/Networking

- [Intel Bluetooth IntelBTPatcher.kext and IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) with BlueToolFixup.kext from [acidanthera/BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM) - after IntelBTPatcher.kext and before IntelBluetoothFirmware.kext
- [AirportItwlm (use in-built WiFi) or itwlm](https://github.com/OpenIntelWireless/itlwm) with [https://github.com/OpenIntelWireless/HeliPort](HeliPort App) (more stable) 
- [IntelMausi](https://github.com/acidanthera/IntelMausi) - Wired Intel Ethernet

## Other

- [RTCMemoryFixup](https://github.com/acidanthera/RTCMemoryFixup) - CMOS emulation
- [HibernationFixUp](https://github.com/acidanthera/HibernationFixup) - RTC variables sync with NVRAM
- [ECEnabler](https://github.com/1Revenger1/ECEnabler) - Embedded Controller for battery status
- [USBToolBox](https://github.com/USBToolBox/kext) - for mapping USB ports
- [YogaSMC](https://github.com/zhen-zen/YogaSMC) - sensors for various hardware and controls for backlit keyboard
- [VoodooI2C](https://github.com/VoodooI2C/VoodooI2C) -  I2C bus device support
- [VoodooPS2](https://github.com/acidanthera/VoodooPS2) - Keyboard, Mouse, Touchpad with gesture support
- [VoodooSMBUS](https://github.com/VoodooSMBus/VoodooSMBus) - ELAN Touchpad support
- [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys) - Brightness Keys
