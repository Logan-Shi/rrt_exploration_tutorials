# rrt_exploration_tutorials
This package is a complementary package for the [rrt_exploration](https://github.com/hasauino/rrt_exploration) ROS package. It provides all the needed Gazebo simulation files to bring up Kobuki robots equipped with laser scanners and ready for the [rrt_exploration](https://github.com/hasauino/rrt_exploration) package. 

## 1. Requirements
The package has been tested on both ROS Kinetic and ROS Indigo, it should work on other distributions like Jade. The following requirements are needed before installing the package:

1- You should have installed a ROS distribution (indigo or later. Recommended is either indigo or kinetic).

2- Created a workspace.

3- Installed the "gmapping" ROS package: on Ubuntu, and if you are running ROS Kinectic, you can do that by typing the following command in the terminal:

```sh
$ sudo apt-get install ros-kinetic-gmapping
```
4- Install ROS navigation stack. You can do that with the following command (assuming Ubuntu, ROS Kinetic):
```sh
$ sudo apt-get install ros-kinetic-navigation
```
5- Install Kobuki robot packages:
```sh
sudo apt-get install ros-kinetic-kobuki ros-kinetic-kobuki-core
sudo apt-get install ros-kinetic-kobuki-gazebo
```
## 2. Installation
Download the package and place it inside the ```/src``` folder in your workspace. And then compile using ```catkin_make```.

## 3. Example

### single exploration using gazebo as simulator

```sh
roslaunch rrt_exploration_tutorials single_simulated_irobotcreate.launch
```

works fine, do not alter

### single exploration using stage as simulator

```sh
roslaunh rrt_exploration_tutorials single_stage_irobot.launch
```

current issue: move_base can't access tf from base_link_laser to map

tf.timestamp error: slam_gmapping using real-time while stage publish sim time

add "use_sim_time = true" in the launch file

### three bots exploration using gazebo as simulator

```sh
mutliple_simulated_house.launch
```

current issue:   
1. map merger works strange, may need to set up init pose  
2. takes up too much cpu resource

### three bots exploration using stage as simulator

```sh
multi_robot.launch
```

current issue:  
1. map merger too slow, need to set up init pose  
2. same issue as single simulator, move_base can't access tf

