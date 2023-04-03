# onshape2gazeboURDF

## Description
Spawn an URDF robot created on OnShape in Gazebo and control it with a joint position controller.

The URDF file requires a few modifications but it mostly works. I used the following OnShape file for testing:
https://cad.onshape.com/documents/75e4e9a14281c074ed3a2c75/w/d9cb7b18558eb661707d2215/e/5577104928fc6d9d013c1b4a

## Requirements
* Xubuntu 20.04
* ROS Noetic
* Gazebo 11
* onShape-to-robot (https://onshape-to-robot.readthedocs.io/en/latest/)

## Dependencies
### onshape-to-robot
* sudo apt install openscad
* sudo apt install meshlab

### Gazebo (in addition to the standard ENPH 353 Linux packages)
* sudo apt install ros-noetic-gazebo-ros-control
* sudo apt install ros-noetic-position-controllers
* sudo apt install ros-noetic-joint-state-publisher
* sudo apt install ros-noetic-effort-controllers

## Usage:

Clone the repo in ros_ws/src
```
cd ros_ws/src
git clone https://github.com/fizzym/onshape2gazeboURDF
```

Compile the packages and source the environment
```
cd ros_ws
catkin_make
source deve/setup.bas
rospack profile
```

Run the packages:
* Terminal 1: ```roslaunch robot_urdf launch_robot_urdf.launch```
* Terminal 2: ```roslaunch robot_controller controller.launch```
* Terminal 3: ```rostopic pub -1 /rrbot/joint1_position_controller/command std_msgs/Float64 "data: 3.0"```
