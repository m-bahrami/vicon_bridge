some high-level python codes that calls broadcasted [tf](http://wiki.ros.org/tf) frames and uses for motion control.





## telloswarm


layered architecture:

- Todo: python scipts that calls  broadcasted tf Pose data. should it be msg or srv? what are the dependecies? 

-  ROS node for motion capture [vicon_bridge](https://github.com/ethz-asl/vicon_bridge), it has one node "vicon" broadcasts tf Pose data (line 503 and 537 in /src/vicon_bridge/src/vicon_bridge.cpp) 

- [TelloPy](https://github.com/m-bahrami/TelloPy) modules establishes Wi-Fi connections with Tello drones to send control commands




## crazyswarm


in /ros_ws/src/

layered architecture:

1) High-level Python scripts:

crazyswarm/scripts/Pycrazyswarm/crazyflieserver.py

publishes control commands in msg and srv formats using the node "CrazyflieAPI" defined in Class CrazyflieServer

2) middle layer ROS node:

crazyswarm/src/crazyswarm_server.cpp

subscribes to msg and srv published in the higher-level Python class

broadcasts motion capture data (line 1117)

3) low-level

/crazyflie_ROS/crazyflie_driver/crazylie_server.cpp

defines ROS msg and srv for the above layers
establishes RADIO connections for crazyflies and manages packet sendings and receiving
