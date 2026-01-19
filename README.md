# my_bot4_js

ROS 2 Jazzy robot package with Gazebo Sim (Harmonic) support.

## Description

This package provides a complete robot simulation setup for ROS 2 Jazzy using Gazebo Sim (Harmonic). It includes:

- Robot description in URDF/Xacro format
- Gazebo Sim integration with ros_gz bridges
- Launch files for simulation and visualization
- RViz configuration files
- Differential drive control
- Lidar and camera sensors

## Dependencies

- ROS 2 Jazzy
- Gazebo Sim (Harmonic)
- ros_gz_sim
- ros_gz_bridge
- ros_gz_image
- robot_state_publisher
- xacro

## Installation

1. Clone this repository into your ROS 2 workspace:
```bash
cd ~/dev_ws_js/src
git clone https://github.com/josemsotov/my_bot4_js.git
```

2. Build the package:
```bash
cd ~/dev_ws_js
colcon build --packages-select my_bot4_js --symlink-install
```

3. Source the workspace:
```bash
source install/setup.bash
```

## Usage

### Launch the simulation

To launch the robot in Gazebo Sim with all bridges:
```bash
ros2 launch my_bot4_js launch_sim.launch.py
```

This will start:
- Gazebo Sim with the robot spawned
- Robot State Publisher
- ROS-Gazebo bridges for cmd_vel, odom, scan, camera, and joint_states

### Launch RViz

To visualize the robot in RViz:
```bash
ros2 launch my_bot4_js rviz.launch.py
```

Or in a separate terminal after launching the simulation:
```bash
rviz2 -d $(ros2 pkg prefix my_bot4_js)/share/my_bot4_js/config/view_bot.rviz
```

### Control the robot

You can control the robot using keyboard teleoperation:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

## Package Structure

```
my_bot4_js/
├── config/          # RViz configuration files
├── description/     # URDF/Xacro robot description files
├── launch/          # Launch files for simulation and visualization
├── worlds/          # Gazebo world files
├── CMakeLists.txt
├── package.xml
└── README.md
```

## Topics

- `/cmd_vel` (geometry_msgs/Twist): Velocity commands for the robot
- `/odom` (nav_msgs/Odometry): Odometry information
- `/scan` (sensor_msgs/LaserScan): Lidar data
- `/camera` (sensor_msgs/Image): Camera image data
- `/joint_states` (sensor_msgs/JointState): Joint state information

## Author

Jose Soto Villasmil - josemsotov@gmail.com

## License

Apache-2.0
