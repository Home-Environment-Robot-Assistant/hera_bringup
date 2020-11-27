# hera_bringup

This package contains launch files and resources to bring up the [HERA (2020 version)](http://robofei.aquinno.com/athome/wp-content/uploads/2020/01/TDP2020ROBOFEI.pdf).

## Dependencies:
* [ROS](https://www.ros.org/) (Melodic Morenia)
  * [roslaunch](http://wiki.ros.org/roslaunch)
  * [rviz](http://wiki.ros.org/rviz)
* [hera_description](https://github.com/Home-Environment-Robot-Assistant/hera_description)
* [hera_control](https://github.com/Home-Environment-Robot-Assistant/hera_control)
* [hera_nav](https://github.com/Home-Environment-Robot-Assistant/hera_nav)

### Configuration:
There are a folder called ```config```, that contains parameters configurations used to visualize the robot.
```
  |-- config
    |-- rviz
      |-- hera.rviz
```

### launch:
There are a folder called ```launch```, that contains files used to bring up and enable interface to the robot using roslaunch in the ROS ecosystem.
```
  |-- launch
    |--bring_up.launch
    |--interface.launch
```
* **bring_up**: Used to bring up the robot. Parameters:
  * **robot_model**: (string, default: hera_full) - Robot used. Available in the [hera_description](https://gitlab.com/fpimentel/hera/hera_description) package.
  * **map_name**: (string, default: empty) - Map name of the environment with the robot is insert. Must be a mapped environment available in the _config/map/_ folder.
  * **use_fake_localization**: (boolean, default: false) - Used in simulated environment if you want an accurate localization. See [hera_nav](https://gitlab.com/fpimentel/hera/hera_nav) for more information.
  * **global_planner**: (string, default: navfn/NavfnROS) - Global planer used to plan the navigation. See [hera_nav](https://gitlab.com/fpimentel/hera/hera_nav) for more information.
  * **local_planner**: (string, default: eband_local_planner/EBandPlannerROS) - Local planner used to navigate. See [hera_nav](https://gitlab.com/fpimentel/hera/hera_nav) for more information.
  * **enable_description**: (boolean, default: true) - Enable/disable load of robot description.
  * **enable_map**: (boolean, default: true) - Enable/disable load of map.
  * **enable_localization**: (boolean, default: true) - Enable/disable localization.
  * **enable_navigation**: (boolean, default: true) - Enable/disable navigation.
* **interface**: Used to enable _rviz_ and _teleop_twist_keyboard_ gui. Parameters:
  * **rviz_file**: (string, default: $(find hera_bringup)/config/rviz/hera.rviz) - Configuration file used in rviz if enable.
  * **enable_gui_rviz**: (boolean, default: true) - Enable/disable rviz gui to visualize the robot.
  * **enable_gui_teleop**: (boolean, default: true) - Enable/disable teleoperation gui to control the robot navigation.

### Resources
There are a folder called ```launch```, that contains the resources used by the robot.
```
  |-- resources
    |-- map
      |-- empty
      |-- simple_room
```
* **map**: Mapped environments available.

# How to use this repository

```bash
roslaunch gazebo_ros empty_world.launch gui:=false
roslaunch hera_bringup bring_up.launch
roslaunch hera_bringup interface.launch 
```
