# Robot simulation in Gazebo
## Robot description

Robot consists of chassis, two wheels and one caster wheel. It is equipped with LIDAR and depth camera.

## Usage
To run simulation:

```
source install/setup.bash
ros2 launch my_bot launch_sim.launch.py world:=./src/my_bot/worlds/cones.world
```

Control using
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```


_Generated from template for ROS package._
