# Discussions:

* micro-ROS derives from ROS2 and differs mainly in the following points:
    * micro-ROS runs on Real-Time Operating System (RTOS) instead of Linux as was the case with ROS2 
    * micro-ROS utilizes Data Distribution Service for Xtremely Resource-Constrained Environments (DDS-XRCE) as compared to the classical Data Distribution Service (DDS) used by ROS2

* micro-ROS vs ROS2 architecture:
![ROS2 Architecture](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/ros2arch.png)
![micro-ROS Architecture](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/microros_arch.png)

* A simple ping=pong application was run to establish basic functionality of the micro-ROS setup, using the Zephyr emulator
