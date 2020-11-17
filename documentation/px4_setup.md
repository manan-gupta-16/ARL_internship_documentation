# Prerequisites

* Linux based system (Ubuntu 20.04 LTS edition)
* NuttX based hardware (Pixhawk flight controller)

## Setting up the Development Environment on Linux system

* Linux allows us with the capability to build and compile the PX4 flight software for all PX4 targets while also allowing support for micro-ROS and ROS2
* Recommended to use Ubuntu based linux flavour for this (LTS 18.04 or 20.04 versions)

* _Caution_: The following build process may not work on top of an existing system

* _Step 1_: Downloading PX4 source code. Use the following terminal command for this

`git clone https://github.com/PX4/PX4-Autopilot.git --recursive`

* _Step 2_: This step involves running the **ubuntu.sh** file in a bash shell for installation of downloaded code

`bash ./Tools/setup/ubuntu.sh`

    * This command has to be run in a bash shell from inside the root directory of the downloaded source code. That is, from inside the PX4-Autopilot directory that is downloaded after the step above. 
    * During the progression of the script, you may be prompted for your sudo password. Type in the same.
    * Since we are planning to use the PX4 Autopilot with micro-ROS and ROS2 and not independently as such, we can use the `--no-sim-tools` flag to omit the simulation tools. This is not necessary though.

* _Step 3_: Once the bash file has run, restart the computer.

* _Step 4_: Upon restarting the computer, the NuttX installation can be confirmed as follows:

`arm-none-eabi-gcc --version` 

* With this we have finished the installation and compilation of the PX4-Autopilot source code. 

## Fast RTPS Installation

* Fast RTPS is a C++ implementation of the Real Time Publish Subscribe protocol. This will be used for communication between the Pixhawk flight controller and an offboard component, for example, an MCU.

* The installation of CMake requires the following tools to be installed in the linux system:
    * CMake, g++, pip3, wget and git
* This can be done by the following command:
`sudo apt install cmake g++ python3-pip wget git`

* The Fast RTPS has dependencies on the following: 
    * Asio ad TinyXML2 libraries
    * OpenSSL
* To install these, run the following commands:  
`sudo apt install libasio-dev libtinyxml2-dev`\
`sudo apt install libssl-dev`

* Now we need to install Fast RTPS from source. Clone the project from GitHub using the following commands:

`git clone --recursive https://github.com/eProsima/Fast-RTPS.git -b 1.8.x ~/FastRTPS-1.8.2`  
`cd ~/FastRTPS-1.8.2`  
`mkdir build`    

* After this, execute the following commands:   
`cmake -DTHIRDPARTY=ON -DSECURITY=ON -DCOMPILE_EXAMPLES=ON`  
`make`  
`sudo make install`  

* The above steps will install Fast RTPS in your computer

## Fast-RTPS-Gen Installation

* We also need to install Fast RTPS-Gen which is the Fast RTPS IDL code generator tool. 

* In order to do this, we need the following packages to be installed
    * Java JDK
    * Gradle

* This requires the Oracle JDK. To check if Oracle Java is already downloaded, use the following command:
`java -version`   
The output should look like:
`java version "1.8.0_241"`  
`Java(TM) SE Runtime Environment (build 1.8.0_241-b07)`  
`Java HotSpot(TM) 64-Bit Server VM (build 25.241-b07, mixed mode)`  

* If this Oracle JDK isn't installed, follow the steps below to install it:

* From the link [here](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html), download the Linux x64 Compressed Archive version, that is, the jdk-15.0.1_linux-x64_bin.tar.gz file.

* After downloading the file, use the following commands in terminal:
`sudo mkdir -p /usr/lib/jvm`  
`sudo tar zxvf jdk-15.0.1_linux-x64_bin.tar.gz -C /usr/lib/jvm`  
`sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk-15.0.1/bin/java" 1`  
If this command gives an error, run it twice  
`sudo update-alternatives --set java /usr/lib/jvm/jdk-15.0.1/bin/java`  

*After this we have to add the path to the installed directory. Use the following command:  
`sudo gedit /etc/environment`  
A file will open after this. At the end of that file, add the following and save the file:  
`JAVA_HOME="usr/lib/jvm/jdk-15.0.1`  
After saving the file close it, and run the following command in the terminal:  
`source /etc/environment`  
* To check this, try this:  
`echo $JAVA_HOME`  
The output should be the path: `JAVA_HOME="usr/lib/jvm/jdk-15.0.1`  
* Finally, check the installation again using:  
`java -version`  

You should get something similar to what is shown in the first step above

* To install Gradle follow the steps below:  
`wget https://downloads.gradle-dn.com/distributions/gradle-6.5.1-bin.zip`  
`unzip gradle-6.5.1-bin.zip`  
`sudo mv gradle-6.5.1 /usr/local/gradle`  

After this, the environment variable has to be setup, using the commands:  

`sudo gedit /etc/profile.d/gradle.sh`  
Add the following line to the flie, save it and close it  
`export PATH=/usr/local/gradle/bin:$PATH`  

The file has to be sourced to apply environment for the current shell  
`source /etc/profile.d/gradle.sh`  

* To test the Gradle installation, type the following:  
`gradle -v`  
It should output the gradle version  












