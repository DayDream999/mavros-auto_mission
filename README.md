# mavros-auto_mission
an simple auto mission for fixed wing aircraft to execute in gazebo with px4 sitl

Resources found at https://github.com/diegomrt/mavros_auto_mission?tab=readme-ov-file, but with some error and indentation problem, modified to be executable.

## Dependencies: ##
1. px4 firmware
2. QGroundControl
3. mavros

runs on Ubuntu20.04 LTS environment, I notice that Ubuntu18 has some issue with QGroundControl, so may need extra work to work around it, but QGC only serves as monitoring method in this mission, not sure if it will run without actually having QGC
steps for running the mission:

1. first terminal launching the gazebo with px4 sitl

```sh
cd ${HOME}/repos/PX4-Autopilot
DONT_RUN=1 make px4_sitl_default gazebo
export PX4_HOME_LAT=40.091754
export PX4_HOME_LON=-3.695714
source ~/catkin_ws/devel/setup.bash    # (optional)
source Tools/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd)/Tools/sitl_gazebo
roslaunch px4 mavros_posix_sitl.launch vehicle:=plane_catapult
```

2. second terminal execute the simple mission

```sh
roslaunch mavros_auto_mission mavros_mission_px4.launch
```
