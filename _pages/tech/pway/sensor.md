---
title:  "Permanent Way RFID Sensor Module"
layout: collection
permalink: /tech/pway/rfid/
entries_layout: grid
classes: wide
sidebar:
  nav: "tech"
---

*NB Refer to [Train Driver Design](/tech/train/design) for more details on train
position tracking. The RFID Sensor module comprises one part of that process.*

## Concept

The RFID Sensor module is a sub-module of the P-Way module. It allows the
P-Way module to sense when trains pass a fixed position on the layout. This is
achieved by attaching RFID tags to each train, one at the front and one at the
back. Locos and brake vans which may be operated in either orientation may
have a tag fitted at each end, giving a full train four location tags in
total, or more for multiple headers. The association between trains and tags
is setup and retained in the Control Panel.

RFID antennae are positioned at certain positions under the track so that
while running a route a train will pass over one periodically. The sensor
then reports the detected tag ID to a P-Way module, and from there it is
relayed to the Train Driver either via DCC or Bluetooth. This allows each
train to regularly recalibrate its own running position, which is tracked
using techniques such as dead reckoning and sleeper counting, each prone
to accumulated error. By regularly resetting its datum the train is able to
maintain an accurate sense of its position. It is important that the latency
between running over a sensor and the train receiving notification is as
low, or at least as predictable as possible.

Sensor locations do not necessarily have to align with block sections, but it
is preferable to have them close to critical features such as line termini
so a train can respond quickly if its accumlated error would otherwise cause
a signal to be passed at danger.

Note that the design places the tag on the train and the reader on the
baseboard for reasons of space. It would be a challenge to fit an effective
reader into smaller gauge trains whereas tiny tags are commonplace.

## Hardware

Each RFID Sensor module comprises a circuit board and an antenna connected
by a short length of cable. It is intended that antennae are positioned above
the trackbed and below the track, while the corresponding circuit board is
located just below the baseboard within reach of short dropper wires.

The antenna will be formed by a thin flexible plastic PCB, and the shape and
size will vary from scale to scale. It is important that a tag can be read
reliably with the train moving at maxumum speed, while a train passing on
a parallel track is not detected.

The circuit will have an RC522 Mifare reader IC coupled with an ESP32 WiFi
module. Each sensor will connect wirelessly to the layout network and take
power from any rail drop making them fast and convenient to connect anywhere
on the layout. This design may be revised if Wireless operation proves
problematic during testing.

It is expected that glass ampoule tags will be used on trains, which are
available as small as 12x3mm making them useful down to N-Gauge stock.
Flat sticker type tags or button tags may be convenient for larger scales.

## Software

Positional events flow as follows:

1. Train passes over sensor generating a positional event.
1. Sensor sends tag ID to Control Panel.
1. Control Panel sends sensor ID to Train Driver.
1. Train Driver recalibrates its position.

The Control Panel may use positional events to trigger other actions, but for
the general case will use continuous positional data provided by the train,
which is separate to the RFID system. The primary purpose of RFID sensing is
to provide trains with regular datums.

RFID Sensor firmware runs on the ESP32 SoC and is responsible for scanning for
tags and then relaying the detected tag 32-bit ID. This is immediately sent to
the Control Panel over the wireless network. The Control Panel maintains a map
of tags so it can lookup which train to notify. Notification may be direct to
the train over Bluetooth or via a DCC channel, subject to performance testing.

Each Train Driver maintains a map of sensor positions so it can identify the
line and offset along that line when it receives an RFID event.
