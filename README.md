# printer-vandal
Configuration and Documentation for the Annex K3

## Installation

Install some headless [RPi OS](https://www.raspberrypi.com/software/), then use [KIAUH](https://github.com/dw-0/kiauh) to install klipper, moonraker, fluidd, and pgcode.


### Flashing the Z-Axis Controller (BTT-SKR 1.4 Turbo)

You can do the configuration step automatically with:

```sh
cp ~/printer_data/config/.bttskr14.config ~/klipper/.config
```

Run `make menuconfig` from the klipper directory, and pick the following options:

1. Architecture: `LPC176x`
2. Processor: `lpc1769 (120MHz)`
3. Bootloader: `16KiB`
4. Interface: `USB`

**Note**: If `make menuconfig` fails because of a set locale error, run this command to fix it: 
`export LC_ALL=en_GB.UTF-8`



**TODO**: Check interop between fluidd and pgcode.

