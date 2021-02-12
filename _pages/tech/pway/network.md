---
title:  "Permanent Way Network Module"
layout: collection
permalink: /tech/pway/network/
entries_layout: grid
classes: wide
sidebar:
  nav: "tech"
---

## Concept

The Network module is a sub-module of the P-Way module. It allows for
different networking standards to be implemented which may change during the
development of Thinking Trains.

Initially it is planned to develop 100Base-T Ethernet and 802.11 WiFi modules.

## Physical Interface

The P-Way network interface comprises two connectors. One or both may be 
utilised by a network module, or two modules may be fitted at once if they
do not require the same connector. Standoffs support rigid mounting of any
configuration and offer convenient alignment with the rear panel for one or
two modules.

Hirose DF9 board-to-board mezzanine connectors are to be used. These are
reliable for high speed signals, repluggable and polarised.

## Hardware Interface

CN1 provides all of the signals required to connect an Ethernet PHY and
magnetics utilising a MAC internal to the P-Way module SoC.

CN2 provides all of the signals required to connect a WiFi SoC such as an
ESP32, or a wired serial connection.

## Software Interface

The P-Way software stack provides an abstraction for communication between
modules so the physical layer can be changed without affecting the rest of the
software stack. Each network module must provide its own abstraction
implementation.

Abstracted functions include discovery, sending and receiving messages to and
from another station and sending and receiving broadcast messages. Two
concurrent interfaces are supported.

## 100Base-T Ethernet Module

The P-Way module SoC has an Ethernet MAC and exposes an RMII interface to the
Ethernet module on CN1. The Ethernet module need provide only a PHY and an
RJ45 connector with integrated magnetics and LEDs.

The network stack for this module runs on the P-Way processor via a network
abstraction.

## 802.11 WiFi Module

For WiFi (or indeed Bluetooth or a similar stack) the networking stack runs on
the network module and interfaces with the P-Way processor via a UART. An
ESP32 SoC with integral antenna will provide this functionality and has the
capability to be extended with Bluetooth functionality, e.g. for direct
communication with trains.

The software for this module has two portions - the ESP32 networking stack
on the module and the network abstraction on the P-Way processor.

