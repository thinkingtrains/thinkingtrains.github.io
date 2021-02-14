---
title:  "Train Driver Module Hardware"
layout: collection
permalink: /tech/train/hw/
entries_layout: grid
classes: wide
sidebar:
  nav: "tech"
---

## Architecture

It is immediately apparently that the primary challenge for the Train Driver
hardware is form factor. Although there is no fixed size for a DCC decoder
module, most 6 pin variants (for N Gauge, i.e. Thinking Trains Type A) are
no wider than 9mm and no longer than 20mm, and that may be too big for some
models. Although there are tricks to fit boards on wire extensions, it's an
important goal for the Train Driver board to be as small as possible.

With this in mind the hardware is designed around a wireless SoC with
sufficient bandwidth to accomodate the railway logic as well as its core
communication tasks. The smallest widely available BLE module known to the
author is 8.5 x 3.5mm including the antenna, and it has one of the more
powerful wireless SoCs. This is ideal.

Larger components such as backup power capacitor and sleeper counter are
pushed out to submodules (with appropriately tiny connectors) to save space
on the main module.

This leaves a power supply capable of regulating the 14V DCC rail power to
drive the motor through an H-Bridge at around 12V, and a 3.3V rail for
everything else.

## Major Components

**BLE Module - Taiyo Yuden EYSHSNZWZ**

This tiny module contains a Nordic nRF52832 with:

* ARM Cortex-M4 @ 64MHz
* 512kB Flash, 64MB RAM
* Timer for DCC decoding
* Timer for PWM output to motor
* I2C for communicating with accessories
* 2.4GHz radio module with BLE 5.2 soft device
* GPIOs to control everything else

**Connectors - Molex Pico-EZmate Slim**

These connectors with 1.2mm pin pitch have a minimal footprint and very small
height dimension. 

A 2-pin variant will connect to the power capacitor:

1. Vbus
2. Ground

A 4-pin variant will connect to accessories:

1. Vbus
2. SCL
3. Gnd
4. SDA

## Form Factor

## Resources
