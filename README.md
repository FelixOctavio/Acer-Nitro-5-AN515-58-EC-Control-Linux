# Acer-Nitro-5-AN515-58-EC-Control-Linux

Implementation of basic EC registers that NitroSense Modifies, as a Bash Script

The script also restores Keyboard RGB Profile set in Windows

Along with setting PL1 and PL2 limits via MSR and MCHBAR

## Features

- [x] Performance Mode
- [x] Fan Mode
- [x] Battery Charging Limit
- [x] Keyboard RGB Control (Per zone control still work in process)
- [x] Windows and Menu Key Lock (On gnome, locked button detected as Play/Pause button)
- [x] Power-Off USB Charging (Not tested)
- [x] Keyboard Backlight Timeout (For quick timeout less than 1 sec, use '66')
- [ ] LCD Overdrive
- [ ] Read Battery Charging Status
- [ ] Read AC Plug Status
- [ ] Read CPU Temp
- [ ] Read GPU Temp
- [ ] Read CPU Fan Speed
- [ ] Read GPU Fan Speed
- [ ] Restore profile after boot

### To-Do:
- [ ] Reformat list command

## Requirements

Kernel Commandline (/etc/default/grub)

```
ec_sys.write_support=1 msr.allow_writes=on
```

## Usage

To show available switches

```
sudo bash nitrosense
```

Available Switches

```
PWR: [q]uiet [d]efault [p]erformance
FAN: [a]uto  [c]ustom  [m]ax
DBG: [r]ead from ec
DBG: [e]nergy data from intel_rapl
DBG: [n]vidia-powerd restart
[b]attery charging limit:
	- [0] - off (100%)
	- [1] - on (80%)
keyboard backlight leve[l]:
	- [0] - 0%
	- [1] - 25%
	- [2] - 50%
	- [3] - 75%
	- [4] - 100%
keyboard backlight c[o]lor:
	- [0] - All zone
	- [1] - Per zone
	- [2] - Dynamic color
[k]eyboard backlight mode:
	- [0] Static
	- [1] Breathing (Dynamic color need to be set)
	- [2] Wave
	- [3] Neon
	- [4] Shifting (Dynamic color need to be set)
	- [5] Zoom (Dynamic color need to be set)
[w]indows and menu key lock:
	- [0] - off
	- [1] - on
Power-off [u]sb charging:
	- [0] - off
	- [1] - on
Keyboard backlight timeou[t]
	- [0] - off
	- [1] - on

```

Example: Default Power with Auto Fan

```
sudo bash nitrosense da
```

Example: Performance Power with Max Fan

```
sudo bash nitrosense pm
```

Example: Performance Power with Custom Fan ( CPU 50% and GPU 75% )

```
sudo bash nitrosense pc 50 75
```

Example: Limit Battery Charging to 80%

```
sudo bash nitrosense b 1
```

Example: Limit Battery Charging to 100%

```
sudo bash nitrosense b 0
```

### Notes

The script also sets a default PL1 and PL2 limit of 95w

Along with PL1 and PL2 Timing of 1 minute

To dump current EC registers

```
sudo bash nitrosense e
```
