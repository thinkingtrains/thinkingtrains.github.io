---
title:  "Train Driver Module Software"
layout: collection
permalink: /tech/train/sw/
entries_layout: grid
classes: wide
sidebar:
  nav: "tech"
---

## Architecture


The Train Driver nRF52832 microcontroller will run the [FreeRTOS](https://www.freertos.org/)
operating system, which is included with the
[Nordic nRF52 SDK](https://www.nordicsemi.com/Software-and-tools/Software/nRF5-SDK).
This is a small kernel with basic multitasking with queues, mutexes and so
on. It is open source with a permissive license, as is the Nordic SDK that
provides a BLE protocol stack and other functions.

The BLE stack runs in a closed source soft device through an API. This leaves
a reasonable amount of bandwidth for running application logic.

## Firmware Loading

During development firmware will be written to flash using an SWD programmer
such as the [Segger JLink](https://www.segger.com/products/debug-probes/j-link/).

In the field, updates will be loaded over the air using the Nordic DFU Service
which is provided with the nRF52 SDK.

## Resources

Github links to follow.
