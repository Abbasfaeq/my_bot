# my_bot

A ROS 2 package for launching the `my_bot` simulation with Gazebo and `ros_gz_bridge`.

## Overview

`my_bot` provides a simple ROS 2 launch package that:

- launches a Gazebo world using `ros_gz_sim`
- loads the robot description from the `description/` directory
- spawns the `my_bot` entity into the Gazebo simulation
- starts a ROS-Gazebo bridge using `ros_gz_bridge`

This package is intended as a starting point for a ROS 2 robot simulation with Gazebo and bridge-based integration.

## Package Contents

- `launch/launch_sim.launch.py` - main simulation launch file
- `launch/rsp.launch.py` - included launch description for robot state publisher or robot setup
- `worlds/empty.world` - default Gazebo world used by the launcher
- `description/` - robot model and URDF/XACRO files
- `config/ros_gz_bridge.yaml` - ROS-Gazebo bridge configuration
- `CMakeLists.txt` / `package.xml` - package build configuration for ROS 2

## Requirements

This package expects a ROS 2 environment with:

- `ros_gz_sim`
- `ros_gz_bridge`
- `ament_cmake`
- standard ROS 2 launch dependencies

## Build

From the workspace root (for example `ros2_ws`):

```bash
colcon build --packages-select my_bot
```

Then source the install setup script:

```bash
source install/setup.bash
```
```

## Run

Launch the simulation with:

```bash
ros2 launch my_bot launch_sim.launch.py
```

The package will:

- start Gazebo with the default `empty.world`
- spawn the `my_bot` robot model using the robot description topic
- start the `ros_gz_bridge` node with the supplied bridge configuration

## Customization

To change the world file, pass a different `world` argument:

```bash
ros2 launch my_bot launch_sim.launch.py world:=/path/to/your/world.sdf
```

To update the robot model or Gazebo description, edit the files in `description/`.

## Notes

- The package is configured for simulation only and does not currently install ROS 2 nodes or executables beyond the launch and bridge setup.
- Ensure `ros_gz_sim` and `ros_gz_bridge` are installed and available in your ROS 2 distribution before launching.

## License

Update `package.xml` and this README with the appropriate license information before publishing.
