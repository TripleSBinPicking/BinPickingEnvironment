# Installation
This document will describe how to get this repository ready to run.
## Preparation steps
Make sure you have the following programs installed:
 - `git` 
 - `ros-melodic` (See the [ROS installation page](http://wiki.ros.org/ROS/Installation). This program was tested with `ros-melodic-desktop` on Ubuntu 18.04)
 - `python-pip` (Included with ROS)
 - [NVidia CUDA toolkit](https://developer.nvidia.com/cuda-10.2-download-archive) (installation instructions can be found [here](https://docs.nvidia.com/cuda/archive/10.2/cuda-installation-guide-linux/index.html), this repository is tested with version `10.2`. A Nvidia GPU is required.)

## Configuring the workspace
1. Create a catkin workspace following the instructions [on the official ROS wiki](http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment).

Execute the following commands in a terminal in the catkin workspace. (Probably `~/catkin_ws/src`)
```bash
$ cd ~/catkin_ws/src
```

2. Clone this repository into the catkin workspace by executing the following command:
```bash
$ git clone --recurse-submodules https://github.com/TripleSBinPicking/bin_picking_environment.git
```

3. Go the the `bin_picking_environment/Deep_Object_Pose` directory and install the python modules:

```bash
$ cd bin_picking_environment/Deep_Object_Pose
$ pip install -r requirements.txt
```

4. Download all the files from [this](https://bit.ly/3S-ABWAC-WEIGHTS) folder and place them in `bin_picking_environment/Deep_Object_Pose/weights` (Only available for people that are affiliated with the project.)

5. Go back to the the `~/catkin_ws` directory in the terminal.
```bash
$ cd ~/catkin_ws
```

6. Install all the dependencies (and install the latest updates):
```bash
$ python -m pip install pyquaternion
$ sudo apt update -qq
$ rosdep update
$ rosdep install --from-paths src --ignore-src -y
```

7. Build the bin picking system, and load the setup into ROS:
```bash
$ catkin_make
$ source devel/setup.bash
```

8. The file structure should look like this:
```
catkin_ws
    |-build
    |-devel
    |-src
    |    |-bin_picking_environment
    |    |    |- Deep_Object_Pose
    |    |    |- documentation
    |    |    |- onrobot_rg2
    |    |    |- robotiq
    |    |    |- triple_s_util
    |    |    |- universal_robot
    |    |    |- Universal_Robots_ROS_Driver
```

Read next:  
[Planning environment explanation](Planning%20Environment%20Explanation.md)
