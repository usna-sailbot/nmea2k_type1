# nmea2k_ros
### D Evangelista, 2020

## Problem statement
The Raspberry Pi is connected to a nmea2k-like CAN bus implementation via a
Pican2 CAN bus shield. We wish to receive nmea2k type messages via the bus
for use in ROS nodes running on the Pi. Possibilities are:
* Rx node translates all nmea2k data into ROS `std_msgs`, `common_msgs`, or appropriate new message types within the project.
* Rx node translates nmea2k into a generic nmea2k Frame type, then specific downstream nodes (launched as needed) parse or decode them
* Do as services instead? 

Open question: How much nmea2k-like stuff should be implemented within ROS with messages passed between nodes or as services, versus how much should be done in Python and not passed between nodes...? 


## Contributors
D Evangelista

## Thanks to
D Evangelista
