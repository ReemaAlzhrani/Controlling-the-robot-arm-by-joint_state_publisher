# Controlling the robot arm by joint state publisher
This project involves controlling a robot arm using the joint_state_publisher in ROS NOETIC . The joint_state_publisher is a ROS package that allows you to publish the state of each joint in a robot arm. This project demonstrates how to set up and control a robot arm by publishing joint states 
---
## prerequisites :
- ROS noetic workspace ( i faced some problems in UBUNTU 20.04 , So i used https://app.theconstruct.ai/ )

---
## Project Setup
### 1. Preparing ROS 
- Install catkin 
```
$ source /opt/ros/noetic/setup.bash
```
- Create a workspace by using catkin_make
```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
$ source devel/setup.bash
```
![1](https://github.com/user-attachments/assets/abb7765e-9a19-45a1-8be0-8128ec99ea2f)
### 2- Installing the package ' arduino_robot_arm '
- Add the “arduino_robot_arm” package to “src” folder
```
	$ cd ~/catkin_ws/src
	$ sudo apt install git
	$ git clone https://github.com/smart-methods/arduino_robot_arm
```
- Installing the dependecies
```
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
$ sudo apt-get install ros-noetic-moveit
$ sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
$ sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
$ catkin_make
```
### 3- Conttrolling the motors 
- To controlling the motors in simulation 
```
$ roslaunch robot_arm_pkg check_motors.launch
```

![2](https://github.com/user-attachments/assets/c9ddff9e-0e17-4f1f-8bad-7f651747d274)
- To open the graph and joints states :
```
$ rqt_graph
$ rostopic echo /joint_states
```

![3](https://github.com/user-attachments/assets/1d61f7c8-064b-420e-9547-d41c019d913d)
![4](https://github.com/user-attachments/assets/1eb34fcf-298f-4fcb-9de9-a852c27410be)
- To lanch gazebo :
```
$ roslaunch robot_arm_pkg check_motors.launch
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
$ rosrun robot_arm_pkg joint_states_to_gazebo.py

```
![5 gazibo](https://github.com/user-attachments/assets/011dcfe7-e154-499a-96d5-6aad4caf287e)
---
## MoveIt Controlling 
```
$ roslaunch moveit_pkg demo.launch
$ roslaunch moveit_pkg demo_gazebo.launch
```
![2nd task - moveit ](https://github.com/user-attachments/assets/f67afa54-dbfd-4858-ac88-c98f3dd5b25e)















