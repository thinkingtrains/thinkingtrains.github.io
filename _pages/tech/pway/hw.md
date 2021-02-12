---
title:  "Permanent Way Module Hardware"
layout: collection
permalink: /tech/pway/hw/
entries_layout: grid
classes: wide
sidebar:
  nav: "tech"
---

## Architecture

The P-Way module is designed to utilise a single microcontroller for most of
its digital functionality. The rest of the circuit is principally power
conversion, protection and interfacing.

The power domain starts with an external 24 - 36VDC supply. This is polarity
protected and fused at 4A with a polyswitch. This is dropped to 14VDC with a
switcher for driving rails, point frogs and accessories. This in turn is
dropped to 5V for driving servos, and to 3.3V for most of the circuitry.

## Major Components

**Microcontroller - ST STM32F427**

* ARM Cortex-M4 @ 168MHz
* 2MB Flash, 256MB RAM
* SDIO memory card interface
* SPI for display
* Timers for rotary decoding
* PWM for servo positioning
* Ethernet MAC
* UART for WiFi & console
* ADCs for current measurement
* GPIOs and hardware timers for bit banging DCC
* GPIOs for everything else

**OLED - ER-OLEDM015-1C-SPI**

* 29x29mm OLED
* 128 x 128 resolution
* 18-bit colour
* SSD1351 controller on SPI

## Form Factor


## Resources
