#Lenovo L480 OpenCore

This cheaply bought laptop beats the hell out of my Macbook 2016 (A1708) except for the screen quality/resolution and the poorer sound output, and lack of aluminium unibody. However the legendary Thinkpad keyboard is light-years ahead, and the nipple too is useful.  These laptops are going cheap, as is the later L580 which is more-or-less identical, so I'd recommend them, definitely. Thanks to everyone involved in OpenCore, the coders, the kext builders, and those who share their setups to help others.

Running Sonoma 14.5 presently, but also worked with Monterey and Ventura previously. The config.plist needs an SMBIOS of MacBookPro 15.

##Hardware
- Intel Core i5 8350
- 2 x 16GB DDR4 2400
- Intel AX210NGW Wifi/Bluetooth	
- 1080P Screen (non-touch)
	
##Working
- Touchpad with multi-point and gestures
- Trackpoint nipple
- Internal Audio Speakers
- Internal Microphone
- Headphone jack output
- Webcam
- Internal 2280 NVME and 2240 NVME plugged into WAN port.
- Wifi/Bluetooth (was Intel 9265 NGW, now using AX210 NGW - no configuration changes necessary for either)
- In-built Ethernet
- Sleep (needs `sudo pmset -a standby 0` to prevent trackpad failing after wake)

##Not Working/Untested
- HDMI Output untested
