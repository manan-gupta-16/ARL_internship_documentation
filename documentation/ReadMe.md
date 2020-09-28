Literature Review and Background :

The underwater and surface robots like STARFISH and NUSwan deployed the in-house developed DSAAV and JC2 framework. These frameworks are custom-built for the vehicles. It is costly to maintain a software framework and this distracts from focusing on robotics research. This poses a problem to harware modularity in the vehicles as the framwework is specifically designed for each vehicles and its application. In other words, each time a modification has to be done, or a new vehicle is designed, the software frameworks have to either be modified a lot or they have to be built from the ground-up. Hence, the idea is to explore using a framework that promotes hardware modularity for the different subsystems.
Another point kept in mind is that the vehicles' different subsystems use microcontroller boards and sentuators (sensors and actuators) to handle their tasks. The vehicle has one central on-board processing unit (for example, a Jetson Nano) which can handle the computationally extensive tasks. 

The Robot Operating System (ROS) provides a framework that offers services for hardware abstraction, implementation of commanly used functionality in robots, message-passing between processes and package management. The ROS2 offers further improvements and capabilities to what was previously part of ROS. However, these run on linux based systems, and hence can't be used in hardware-constrained environments like microcontroller boards used in the vehicles.

The Idea:

Here comes micro-ROS (uROS), which offers major changes as compared to ROS2, with the most important one being that it uses a Real-Time Operating System (RTOS) to run. This allows the usage of ROS based applications in microcontroller boards. micro-ROS also deploys DDS (Data Distribution Service) for eXtremely Resource Constrained Environments (DDS-XRCE), instead of the classical DDS.
Not only can micro-ROS be used on microcontroller boards, it also provides support for the ROS2 stack. This allows communication of micro-ROS applications with ROS2 agents.
This supports the development of "loosely coupled systems" in the vehicles; meaning the development of different subsystems can be done independent of the others. 
Hence, using uROS applications to use sentuators interfaced with microcontrollers should allow for reusable code and hardware modularity. 
