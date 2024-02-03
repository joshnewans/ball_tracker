# ball_tracker

This repository contains a simple demonstration of using ROS and OpenCV to track a ball with a mobile robot via a camera feed.

The associated tutorial is available [here](https://youtu.be/gISSSbYUZag).

Thanks very much to Tiziano Fiorenzani for his [ROS 1 tutorial](https://www.youtube.com/watch?v=We6CQHhhOFo) and [corresponding code](https://github.com/tizianofiorenzani/ros_tutorials/blob/master/opencv/src/find_ball.py) on which this repo is based (code reproduced with permission).

One other thing to be wary of: this is a ROS/ament Python package, which means the launch and config files contained will NOT be linked with the `--symlink-install` command for colcon, and will need to be rebuilt after changes.

Remove warning triggers regarding setuptools by downgrading the version:
`pip install setuptools==58.2.0`

## Getting started

A launch file and example parameters are provided.

Clone this repo into your ~/dev_ws/src/ folder:
```
git clone git@github.com:joshnewans/ball_tracker.git
```

Preliminary tuning mode (remember to source foxy and workspace):
```
ros2 run ball_tracker detect_ball --ros-args -p tuning_mode:=true -r image_in:=camera/image_raw
```
rviz2: add `Image` -> `Topic: /image_out`

Record those parameters!

Get detect ball's point measurements:
```
ros2 topic echo /detected_ball
```

3D ball location estimation:
```
ros2 run ball_tracker detect_ball_3d
```
rviz2: add `Marker` -> `Topic: /ball_3d_marker`

Follow the ball:
```
ros2 run ball_tracker follow_ball --ros-args -r cmd_vel:=cmd_vel_tracker
```

Copy `ball_tracker_params_example.yaml` into your main ros package config folder.
Rename it to `ball_tracker_params_sim.yaml` with the appropriate tuning parameters.

Then you can launch:
```
ros2 launch ball_tracker ball_tracker.launch.py params_file:=src/<main_ros_package_name>/config/ball_tracker_params_sim.yaml enable_3d_track:=true
```

## Nodes

TODO Document them

## Known issues
- Can't easily detect red due to hue wrap. If you need to detect red robustly you'll need to go in and mess with the HSV filtering.
