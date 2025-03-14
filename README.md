## Instructions
### Docker container
* To open running container bash
```bash
docker ps
docker exec -it <container id> bash
```
* To activate the `ros2` terminal command, use
```bash
source /opt/ros/$ROS_DISTRO/setup.bash
```
### turtlebot3
* workspace is
```bash
cd ~/turtlebot3_ws
```
* [tutorial link](https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation)
* launch my world
```bash
ros2 launch turtlebot3_gazebo world.launch.py
```
* start SLAM, run teleop and then save the map
```bash
ros2 launch slam_toolbox online_async_launch.py
ros2 run turtlebot3_teleop teleop_keyboard
ros2 run nav2_map_server map_saver_cli -f /home/ws/src/my_map
```
* launch map
```bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py map:=/home/ws/src/my_map.yaml
```
