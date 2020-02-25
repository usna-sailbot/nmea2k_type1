# nmea2k_type1
### D Evangelista, 2020

## Problem statement
The Raspberry Pi is connected to a nmea2k-like CAN bus implementation via a
Pican2 CAN bus shield. We wish to receive nmea2k type messages via the bus
for use in ROS nodes running on the Pi. Possibilities are:
* Rx node translates all nmea2k data into ROS `std_msgs`, `common_msgs`, or appropriate new message types within the project (no nmea2k internals are exposed to ROS).
* Rx node translates nmea2k into a generic nmea2k `Frame` message, then specific downstream nodes (launched as needed) parse or decode them
* Do as services instead? 
* Do we need the ability for ROS to have various virtual nmea2k nodes sharing the hardware node (may be useful for simulation or debugging). 

Open question: How much nmea2k-like stuff should be implemented within ROS with messages passed between nodes or as services, versus how much should be done in Python and not passed between nodes...? 

## Prerequisites
The hardware layer follows the example here: [[https://github.com/skpang/PiCAN-Python-examples]], which requires installation of `python-can`. To install `python-can`, as `sudo`:
```bash
pip3 install --upgrade python-can
```

Alternatively, on the Pi, follow the instructions here [[http://skpang.co.uk/blog/archives/1220]], in which the overlay for the Pican2 hardware is added and a specific version of Python-CAN is installed from [[https://bitbucket.org/hardbyte/python-can/get/4085cffd2519.zip]] using the `python3` `setuptools` (i.e. run the included `setup.py`). 

## Evangelista guess, Feb 2020
I think we're going to want to be able to have one hardware Pican2 interface shared among various virtual nmea2k devices so I'm going to try writing that first.I'll call this **type 2 nmea2k** and is addressed elsewhere, see [[https://github.com/usna-sailbot/nmea2k_type2]].

As an alternative, if that's too big or too slow, maybe I'll also try a compact pure Python layer on top of the Pican2 hardware that spits out ROS std_msgs? I'll call this **type 1 nmea2k** and it is the subject of this repository. 

## Contributors
D Evangelista

## Thanks to
D Evangelista
