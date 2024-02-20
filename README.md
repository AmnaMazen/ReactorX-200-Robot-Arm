# ReactorX-200-Robot-Arm
In this repository, we will provide step-by-step tutorials for ReactorX-200 Robot Arm. This work is done with the collaboration of my student: Chenghao Lin


## Installation
For ROS Melodic installed on Ubuntu 18.04

$ sudo apt install curl

$ curl 'https://raw.githubusercontent.com/Interbotix/interbotix_ros_manipulators/main/interbotix_ros_xsarms/install/rpi4/xsarm_rpi4_install.sh' > xsarm_rpi4_install.sh

$ chmod +x xsarm_rpi4_install.sh

$ ./xsarm_rpi4_install.sh -d melodic

You will get three questions during the installation, one about installation vision packages and another about installing MATLAB demos I accepted both of them by typing "y" in the terminal followed by "Enter key".

You may get an error about missing packages such as "dynamixel-sdk"

You will solve this error by installing this packages using the following command structure:

$ sudo apt-get install ros-melodic-\<package-name\>

In case of "dynamixel-sdk"

$ sudo apt-get install ros-melodic-dynamixel-sdk


Note: You may need to replace every "_" with "-" in the name of the package. 

Now rerun the installation again:

$ ./xsarm_rpi4_install.sh -d melodic

### Build the workspace by catkin_make

$ cd ~/interbotix_ws

$ catkin_make

I got this error : "Could not find a package configuration file provided by "moveit_commander"
  with any of the following names:

    moveit_commanderConfig.cmake
    moveit_commander-config.cmake
"

I solved it by running 

$ sudo apt-get install ros-melodic-moveit-commander

Try again building

$ catkin_make

I got this error " Could not find a package configuration file provided by "apriltag_ros" with
  any of the following names:

    apriltag_rosConfig.cmake
    apriltag_ros-config.cmake
"

I solved it by running 

$ sudo apt-get install ros-melodic-apriltag-ros

I got this error "Could not find a package configuration file provided by
  "joint_trajectory_controller" with any of the following names:

    joint_trajectory_controllerConfig.cmake
    joint_trajectory_controller-config.cmake
"
I solved it by running 

$ sudo apt-get install ros-melodic-joint-trajectory-controller

I had similar error for other packages that can be solved using those commands:

$ sudo apt-get install ros-melodic-moveit-visual-tools

$ sudo apt-get install ros-melodic-realsense2-camera

$ sudo apt-get install ros-melodic-effort-controllers


## Installation checks

After running the installation script on the robot computer, we can verify that the script ran successfully.

### udev Rules

Check that the udev rules were configured correctly and that they are triggered by the U2D2. This can be done by checking that the port name shows up as ttyDXL when the U2D2 is plugged into a USB port. The command and the expected output are below:

$ ls /dev | grep ttyDXL

Output should be 

ttyDXL

### Interbotix ROS Packages

Check that the Interbotix ROS packages were installed correctly. The command and example output are below:

$ source /opt/ros/melodic/setup.bash

$ source ~/interbotix_ws/devel/setup.bash

Make sure that you have three packages: interbotix_xs_sdk, interbotix_xs_msgs, and interbotix_xs_modules

$ rospack list | grep interbotix_xs_sdk

$ rospack list | grep interbotix_xs_msgs

$ rospack list | grep interbotix_xs_modules


## Launch the rx200 arm in RViz 

$ roslaunch interbotix_xsarm_descriptions xsarm_description.launch robot_model:=rx200 use_joint_pub_gui:=true

## Get familiar with the physical robot arm (rx200) by executing the following command in the terminal:

$ source ~/interbotix_ws/devel/setup.bash

$ roslaunch interbotix_xsarm_control xsarm_control.launch robot_model:=rx200

## The Last step here is to enable and disable the torque using the rosservice

Open new Terminal

$ source ~/interbotix_ws/devel/setup.bash

$ rosservice call /rx200/torque_enable "{cmd_type: 'group', name: 'all', enable: false}"






