# Yackboard ([Y]et [A]nother [C]ustom [K]ey Board)

This is an experimental fork of the [ZMK Project](https://www.github.com/zmkfirmware/zmk) tailored to the
[Yackboard](http://gitlab.com/voidyourwarranty/yackboard). You will get the keys with my layout work easily and with
some knowledge of ZMK also manage to change the keymap, but mouse devices still require programming.

The present fork was created on 2022-11-26 from the `main` branch at https://github.com/zmkfirmware/zmk with the mouse
functions branch `mouse-ftc` of https://github.com/ftc/zmk and the Pimoroni PIM 447 track ball branch `mouse-pim447` of
https://github.com/cdc-mkb/zmk merged in.

## New Shields

The shield `twobytwo3` is a proof of principle with the following features:
- split wireless keyboard with Nice!Nano controller on each half
- 2x2 keyboard matrix on each half: rows on pins 15,14; columns on pins 16,10; diodes from row to column
- right half has got a Pimoroni PM447 Track Ball with SDA on pin 2, SCL on pin 3, INT not connected (all pin numbers
  above use the Pro Micro numbering)

The shield `yackboard` drives the keys of the actual Yackboard:
- split wireless keyboard with Nice!Nano controllers on each half
- 5x5 keyboard matrix with 23 switches mounted on each half
- right half has got a Pimoroni PM447 Track Ball with SDA on pin 2, SCL on pin 3, INT not connected (all pin numbers
  above use the Pro Micro numbering which agrees with the numbers on the silkscreen of the PCB next to the extra 10 pin
  header)

## Improved Driver

I have extended the Pimoroni PIM 447 track ball driver and implemented inertia, acceleration depending on the immediate
past which allows some balance between precision locally and fast movement over large distances. I have made the new
parameters configurable from the device tree. The shield `twobytwo3` contains a sample configuration.

The track ball option `power-layer` can now be set in order to make the track ball driver and 3V3 power output of the
Nice!Nano depend on activation of a given layer. Also, `idle-timeout` activates a timer that resets the keyboard to the
default layer after a given idle period in seconds. These options were added because the track ball has too large an
idle power draw to remain powered on all the time on a wireless keyboard.

The following is the original README of the ZMK Project:

## Zephyr™ Mechanical Keyboard (ZMK) Firmware

[![Discord](https://img.shields.io/discord/719497620560543766)](https://zmk.dev/community/discord/invite)
[![Build](https://github.com/zmkfirmware/zmk/workflows/Build/badge.svg)](https://github.com/zmkfirmware/zmk/actions)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](CODE_OF_CONDUCT.md)

[ZMK Firmware](https://zmk.dev/) is an open source (MIT) keyboard firmware built on the [Zephyr™ Project](https://www.zephyrproject.org/) Real Time Operating System (RTOS). ZMK's goal is to provide a modern, wireless, and powerful firmware free of licensing issues.

Check out the website to learn more: https://zmk.dev/

You can also come join our [ZMK Discord Server](https://zmk.dev/community/discord/invite)

To review features, check out the [feature overview](https://zmk.dev/docs/). ZMK is under active development, and new features are listed with the [enhancement label](https://github.com/zmkfirmware/zmk/issues?q=is%3Aissue+is%3Aopen+label%3Aenhancement) in GitHub. Please feel free to add 👍 to the issue description of any requests to upvote the feature.
