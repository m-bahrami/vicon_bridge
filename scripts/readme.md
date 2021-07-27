some high-level python codes that calls broadcasted [tf](http://wiki.ros.org/tf) frames and uses for motion control.













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
