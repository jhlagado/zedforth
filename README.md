# zedforth

I'm currently exploring some options. If you are looking for the original STC zedForth the [go here](https://github.com/jhlagado/zedforth/tree/pause).

## import this repo into asm80.com

- click `Import repo from GitHub` button
- paste `https://github.com/jhlagado/zedforth` into the`Enter https GitHub link` text field.

## to run app

- select the `MAIN.z80` file
- press `Emulator [F10]` button

## to run tests

- select the `TEST.z80` file
- press `Emulator [F10]` button

## to debug

- comment out line 1:

```asm
  ; .engine mycomputer
```

in `main.z80` or `main-test.z80` files

## Using a Mac to program an 8K AT28C64B-15PU EEPROM

### truncate to 8192

head -c 8192 main.z80.bin > x.bin

### program to minipro

minipro -p AT28C64B -w x.bin

## Using a Mac to connect serially to the Southern Cross

Open an OS X terminal session (window)
Find the right TTY device. Type:

```bash
ls /dev/cu.*
```

With the USB-Serial adapter plugged in, you'll get a list, including something like this:

```bash
ls /dev/cu.*
```

```bash
/dev/cu.Bluetooth-Incoming-Port	/dev/cu.usbserial-AI03T2RU
```

If you don't have a usb serial device, [install this driver](https://pbxbook.com/other/sw/PL2303_MacOSX_1_6_0.zip):

To use a driver, for example, the bit-banged interface which runs at 4800 baud type:

```bash
screen /dev/cu.usbserial-AI03T2RU 4800
```

To bring up the monitor on the Southern Cross, press the `Fn` key twice.

you should then see:

```bash
SCM 1.5 SERIAL MONITOR
ACCEPTS ONLY UPPER CASE - H FOR COMMAND LIST
>
```

To communicate with the Southern Cross SCC-SERIAL-LCD card use 115200 baud e.g.

```bash
screen /dev/cu.usbserial-AI03T2RU 115200
```
