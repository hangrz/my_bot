# Robot simulation in Gazebo
## Robot description

Robot consists of chassis, two wheels and one caster wheel. It is equipped with LIDAR and depth camera.

## Usage
To run simulation:

```
source install/setup.bash
ros2 launch my_bot launch_sim.launch.py world:=./src/my_bot/worlds/cones.world
```

Rviz visualization
```
rviz2 -d ./src/my_bot/config/view_bot.rviz 
```

Control using
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

Map creation
```
rviz2 -d src/my_bot/config/drive_bot.rviz

ros2 launch slam_toolbox online_async_launch.py slam_params_file:=./src/my_bot/config/mapper_params_online_async.yaml use_sim_time:=true

ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped
```

Mapping serwer - AMCL
```
ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=my_map1_save.yaml -p use_sim_time:=true

ros2 run nav2_util lifecycle_bringup map_server

ros2 run nav2_amcl amcl --ros-args -p use_sim_time:=true

ros2 run nav2_util lifecycle_bringup amcl
```

_Generated from template for ROS package._
