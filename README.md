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

Then run `make` to build the firmware. Grab that from the printer with `scp vandal:klipper/out/klipper.bin firmware.bin`, and then copy it onto the microSD card. Hit the reset button to flash the firmware. The firmware ID should be:

```
/dev/serial/by-id/usb-Klipper_lpc1769_0A60FF0D22813AAFF5116A5CC12000F5-if00
```


### Flashing the XY-Axis Controller (Constellation Supernova)

You can do the configuration step automatically with:

```sh
cp ~/printer_data/config/.supernova.config ~/klipper/.config
```

Run `make menuconfig` from the klipper directory, and pick the following options:

1. Architecture: `RP2040`
2. Bootloader: `0`
3. Interface: `USB`

Then run `make` to build the firmware. Grab that from the printer with `scp vandal:klipper/out/klipper.uf2 klipper.uf2`, connect the RP2040 to the computer via a USB B Micro cable while holding down the boot button, and then copy it onto the device. Connect the device back to the Raspberry Pi. The firmware ID should be:

```
/dev/serial/by-id/usb-Klipper_rp2040_E6609103C3335822-if00
```

## TODO

- Check interop between fluidd and pgcode.

