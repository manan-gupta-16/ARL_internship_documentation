# Discussions:

### PX4 Autopilot Software

* PX4 is an open-source research platform drones, underwater vehicles and boats. [Documentation](https://docs.px4.io/master/en/index.html)

* Looking towards more complex systems, the PX4 platform will become a subsystem in a larger system, such as one using ROS2. Hence, a bridge is implemented that allows PX4 uORB (Object Request Broker) publisher/subscriber architecture to connect to RTPS protocol participants over the same DDS standard layer. px4_ros_com is a ROS2 package for bridging PX4 and ROS2 throug a micro-RTPS bridge. [Package Link](https://github.com/PX4/px4_ros_com)

* ![PX4 to ROS2](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/PX4_to_ROS2.png)

* Instead of the FastRTPS protocol being used for the bridge, the Micro XRCE-DDS can be used. Advantages of bringing DDS to PX4:
    * Sacalable architecture
    * Eases integration of PX4 into ROS 2: Straightforward many-to-many data exchange between PX4 internals and DDS/ROS 2
    * Optimally performing middleware for time-critical applications
    The client library is dynamic and static memory free

* A second version of the PX4-ROS2 bridge shown above is implemented with micro XRCE-DDS as follows:

* ![Bridge version 2](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/PX4-ROS%40_Bridge_v2.png)

* This also allows us to bring in support for micro-ROS based applications, using the micro-ROS XRCE-DDS agent and client

* ![micro-ROS and PX4 bridge](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/microROS-PX4_bridge.png)

### Other Points:

* The PX4 has a system console feature allowing low-level access to the system. This can be used for low-level debugging/development. A similar console called NSH system console is provided by NuttX RTOS. They have given a tutorial for the same where it can be tried and run on the Olimex board here: [link](https://micro-ros.github.io/docs/tutorials/advanced/nuttx/nsh/)

* Micro XRCE-DDS Memory Profiling: [Link](https://www.eprosima.com/index.php/resources-all/performance/micro-xrce-dds-memory-profiling)
The results obtained show that memory consumption of uROS agent can be supported by MCU with RAM memory on the order of ~ 300-400 KB and flash of less than 500 KB

* Research paper which discusses the implementation of Real-Time Publish-Subscribe (RTPS) for uCs in robotic applications. RTPS is the underlying protocol for DDS. [Paper Link](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/Research%20Papers%20Reviewed/RTPS_MCUs.pdf). We can try its implementation on hardware here: [link](https://github.com/manan-gupta-16/embeddedRTPS-STM32)

* The PX4 has a system console feature allowing low-level access to the system. This can be used for low-level debugging/development. A similar console called NSH system console is provided by NuttX RTOS. They have given a tutorial for the same where it can be tried and run on the Olimex board here: [link](https://micro-ros.github.io/docs/tutorials/advanced/nuttx/nsh/)

### Previous Discussions:

* micro-ROS derives from ROS2 and differs mainly in the following points:
    * micro-ROS runs on Real-Time Operating System (RTOS) instead of Linux as was the case with ROS2 
    * micro-ROS utilizes Data Distribution Service for Xtremely Resource-Constrained Environments (DDS-XRCE) as compared to the classical Data Distribution Service (DDS) used by ROS2

* ROS2 vs micro-ROS2 architecture:

* ![ROS2 Architecture](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/ros2arch.png)
![micro-ROS Architecture](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/microros_arch.png)

* A simple ping-pong application was run to establish basic functionality of the micro-ROS setup, using the Zephyr emulator
    * The first step was to flash the firmware
    * ![ping-pong application flashed](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/ping_pong_test_1.png)
    * The second step was to check if the node was publishing pings
    * ![ROS2 subscribed to pings](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/ping_pong_test_2.png)
    * To have the micro-ROS application to publish pongs, a fake_ping was sent to it, and the response received was read
    * ![fake_ping sent](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/ping_pong_test_3.png)
    * ![pong received](https://github.com/manan-gupta-16/ARL_internship_documentation/blob/master/documentation/Images/ping_pong_test_4.png)

* micro-ROS applications running on microcontroller units (MCUs) deploying RTOS can interface with other computers/microprocessors/MCUs using a agent run using ROS2. The agent is a ROS2 node that wraps the Micro XRCE-DDS agent. Using this, micro-ROS nodes can communicate with the ROS2 world and the DDS global data space. Peer-to-Peer (P2P) communication between different micro-ROS nodes running on the same or different MCU is also possible using this agent. [Micro XRCE-DDS Agent](https://github.com/eProsima/Micro-XRCE-DDS-Agent)

* Clients - XRCE entities on low-resource consumption devices
* Agents - XRCE entity connected with DDS global data space. Acts on behalf of Clients in the DDS world



