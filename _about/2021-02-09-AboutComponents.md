---
layout: single
title:  "Thinking Trains Main Components"
date:   2021-02-09 23:17:00
---

Thinking Trains comprises several components which will be tackled in turn,
consecutively, or as and when the mood takes me! Broadly these comprise:

## Permanent Way

The Permanent Way module is a control interface for trackwork and
signalling infrastructure. It converts abstract instructions from the Control
Panel (such as setting a route) to specific actions on the layout (just as
moving points and signals). Its main responsibilities are:

* Accept commands from the Control Panel.
* Provide power to the track and elsewhere on the layout.
* Send rail data such as block identification and signal states.
* Set and sense points (turnouts / switches).
* Set signals.

## Train Driver

The Train Driver module is the "brains" of a train. It derives situational
awareness (such as train position, signal states and speed limits) and
responds by moving or stopping the train according to a programmed set of
rules. In essence it simulates the behaviour of a real train driver, but
without all the tea drinking. Its main responsibilities are:

* Implement train driving logic (the "expert machine").
* Derive the position of the train, including block number and distance within a block.
* Respond to signals, speed limits and shunt instructions.
* Set the train speed and direction of travel.
* Control any lighting, sound and other effects that the model has available.
* Respond to manual reversion (direct control by an operator).

## Control Panel

The Control Panel module is the primary human interface for Thinking Trains.
The system is initially configured here, including track layout, loco details,
routes and connected hardware. During standard operation the user interface
will resemble a real world control and mimic panel from which the operator can set
and clear down routes. The operator can also communicate directly with trains,
e.g. to provide shunt instructions or for manual reversion. Its main
responsibilities are:

* Provide the user interface.
* Communicate with Permanent Way to control and monitor routes.
* Communicate with Train Driver to control and monitor trains.
* Automate railway operation.

## Kings Cross Layout

Although several small test tracks will likely be required to assist with the
development and testing of Thinking Trains, the final goal is to create a
fully functional demonstration layout to showcase all of the features. The
layout must be fun and interesting in its own right, otherwise what's the
point?

The plan is to construct a closely scaled layout of Kings Cross station (London,
England) including the station approach circa 2018 (before major remodelling
of the station throat that moved most of the pointwork downline beyond the gas
works tunnels). This is quite a complex layout but can be fitted in approximately
4.5m (15ft) x 1m (3ft) with full length platforms using N gauge. Reasonably
prototypical pointwork can be assembled with off-the-shelf Peco Code 55 products.

Beyond the tunnel entrance will be a helix to move the four running lines to a
lower level, where they will fan out into a fiddle yard below the main layout. It
should be possible to run many prototypical operations and timetables from the
era. The hope is that Thinking Trains will lend itself to end-to-end running far
better than traditional control.

The layout will reflect the technological goals of the project with an unusual
aesthetic, more akin to an architect's model than a traditional model railway.
This is certain to upset some people in the hobby! Hopefully the end result
will be a unique model in multiple ways - or at least it'll be striking!
