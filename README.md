# sample project for AVR on Meson

that simple
tested on and for a knock-off Arduino UNO R3 with some weird possibly ATMega clone???
(ATMega328PB-based UNO R3 clone with CH340 serial bridge)
idk

im tired

## Instructions:
The whole thing depends on the cross compilation file to be set up properly,
if you use anything other than the ATmega328PB, you'll need to change the file
to the right MCU in the `-mmcu=` flag and reconfigure meson/re-setup meson

after that, all sources that must be build will be in `src` with  a `meson.build`
returning `sources` there, add to it for anything else necessary

In the main `meson.build` there is the required things to build the final elf and
flash it with a custom target, the relevant options are:

- programmer
    what programmer protocol should be used by avrdude, if you just want to use an arduino with it, set to `arduino`, default is `urclock`
- processor
    What processor will avrdude try to flash to, default is `atmega328pb`, change to `atmega328p` or `m328p` for Arduino
- port
    The port avrdude will try to communicate over, `/dev/ttyUSB0` is the default, change as necessary
- memory
    What memory part will avrdude try to flash to, `flash` is the default

### Building:
The project comes with a simple blink program in `src/main.c`
`meson compile` will build the program
`meson compile flash` will flash the program and rebuild if necessary

Really, that's it! should be easily expansible if you need any more

## Changelog
[changelog.md]
