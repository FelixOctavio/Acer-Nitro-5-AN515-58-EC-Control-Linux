# Acer-Nitro-5-AN515-58-EC-Control-Linux

Implementation of basic EC registers that NitroSense Modifies, as a Bash Script

The script also restores Keyboard RGB Profile set in Windows

Along with setting PL1 and PL2 limits via MSR and MCHBAR

# Requirements

Kernel Commandline (/etc/default/grub)

```
ec_sys.write_support=1 msr.allow_writes=on
```

# Usage

To show available switches

```
sudo bash nitrosense
```

Available Switches

```
PWR:  [q]uiet [d]efault [p]erformance
FAN:  [a]uto  [c]ustom  [m]ax
DBG:  [r]ead from ec
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

# Notes

The script also sets a default PL1 and PL2 limit of 95w

Along with PL1 and PL2 Timing of 1 minute

To dump current EC registers

```
sudo bash nitrosense e
```
