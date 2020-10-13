## Steps for Setting Up the micro-ROS environment:

* micro-ROS applications are supported by three RTOSes for providing the capability to run on microcontroller boards.

* It also has a provision for installing the necessary framework and tools on a linux system.

* However, since our aim is to explore the practicality of working with micro-ROS on limited hardware, we will work with an RTOS environment. To do this, we will setup the Zephyr emulator (open-source Zephyr RTOS which can be setup as an emulator on any Ubuntu 20.04 LTS computer system). This allows us to work on applications on computer systems without having the need to work with microcontrollers everytime, while simulatng the expected behaviour.

* [Know more about Zephyr emulator](https://docs.zephyrproject.org/latest/boards/posix/native_posix/doc/index.html)

* Follow [these](https://micro-ros.github.io/docs/tutorials/advanced/zephyr_emulator/) steps to setup the micro-ROS environment on your Ubuntu 20.04 LTS computer. 

* Prerequisites require installing ROS 2 Foxy FitzRoy from [here](https://index.ros.org/doc/ros2/Installation/Foxy/Linux-Install-Debians/)

* The micro-ROS setup finally works through a simple ping-pong application to test the system. It concludes with a test for a multi-node application.

### Caution:

* When setting up the micro-ROS and ROS2 environment on your computer system, make sure you setup ROS2 to start with.

* If you first setup micro-ROS for linux based applications or already have it installed on your computer, then you might face issues while setting up the environment for the Zephyr emulator directly using the steps above. In such a case, you can use a Docker container to setup the Zephyr emulator, to prevent clashes with the other setup for linux.