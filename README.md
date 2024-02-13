# ReactorX-200-Robot-Arm
In this repository, we will provide step-by-step tutorials for ReactorX-200 Robot Arm


## Installation
For ROS Melodic installed on Ubuntu 18.04

$ sudo apt install curl

$ curl 'https://raw.githubusercontent.com/Interbotix/interbotix_ros_manipulators/main/interbotix_ros_xsarms/install/rpi4/xsarm_rpi4_install.sh' > xsarm_rpi4_install.sh

$ chmod +x xsarm_rpi4_install.sh

$ ./xsarm_rpi4_install.sh -d melodic

You will get three questions during the installation, one about installation vision packages and another about installing MATLAB demos I accepted both of them by typing "y" in the terminal followed by "Enter key".

You may get an error about missing packages such as "dynamixel-sdk"

You will solve this error by installing this packages using the following command structure:

$ sudo apt-get install ros-melodic-<package-name>

In case of "dynamixel-sdk"

$ sudo apt-get install ros-melodic-dynamixel-sdk


Note: You may need to replace every "_" with "-" in the name of the package. 

Now rerun the installation again:

$ ./xsarm_rpi4_install.sh -d melodic

