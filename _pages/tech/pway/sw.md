---
title:  "Permanent Way Module Software"
layout: collection
permalink: /tech/pway/sw/
entries_layout: grid
classes: wide
sidebar:
  nav: "tech"
---

## Architecture

The P-Way module microcontroller will run the [NuttX](https://nuttx.apache.org/)
RTOS. This is a Posix-like threaded OS with a mature driver tree for STM32F4
and proven reliability in complex applications. It is open source with a
permissive license.

## Firmware Loading

During development firmware will be written to flash using an SWD programmer
such as the [ST-Link](https://uk.farnell.com/stmicroelectronics/st-link-v2/icd-programmer-for-stm8-stm32/dp/1892523).

In the field, updates will be loaded from SD card (either manually copied to
the card or loaded over the network). To accommodate this a bootloader will
be located at the start of flash and not normally written to (it may be
locked down). It starts the main application, located further into Flash,
or writes a new update to flash as appropriate.

The bootloader is a minimal NuttX build with just enough functionality for its
tasks.

## Best Practice

Functionality will be added in a modular fashion such that each component may
be included or excluded without affecting other components where no critical
dependency exists.

In so much as multiple threads are desirable for P-Way (which has diverse
responsibilities with asynchronous data sources) all inter-thread operations
will route through thread-safe message queues.

Fast time-critical operations such as bitbanging the DCC protocol will be
scheduled by hardware timers and run under interrupts. Any lengthy
operations will always be queued down to the task, even if triggered under
interrupt.

## Resources

Github links to follow.
