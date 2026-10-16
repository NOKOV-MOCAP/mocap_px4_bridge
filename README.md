# Mocap-PX4 Bridge

This ROS 2 Package takes the Position and Orientation measurements from Nokov system and send them to PX4 through the [uXRCE-DDS](https://docs.px4.io/main/en/middleware/uxrce_dds.html) bridge between ROS 2 and PX4.

## Getting started

We will create a ROS 2 workspace in `~/ros2_ws`, clone the required packages, build, and run:

```shell
mkdir -p ~/ros2_ws/src/
cd ~/ros2_ws/src/
git clone -b ros2 https://github.com/NOKOV-MOCAP/mocap_nokov.git
git clone https://github.com/NOKOV-MOCAP/mocap_px4_bridge.git
git clone https://github.com/PX4/px4_msgs.git
cd ~/ros2_ws
colcon build --symlink-install
source ~/ros2_ws/install/setup.sh
ros2 launch mocap_px4_bridge launch.py 
```

## Changing the topics names

By default:

1. This package subscribes to Nokov measurement data published on a topic named after the robot’s rigid body name as defined in the Motive application. For example, if the robot was named cf_1 in Motive, the corresponding topic will be `/cf_1/pose`.
2. Publish the measurements to the topic `/fmu/in/vehicle_visual_odometry`

To change the names of these topic, you need to edit the file `config/params.yaml`.
