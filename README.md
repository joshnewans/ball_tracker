# ball_tracker

This repository contains a simple demonstration of using ROS and OpenCV to track a ball with a mobile robot via a camera feed.

The associated tutorial is available [here](https://youtu.be/gISSSbYUZag).

Thanks very much to Tiziano Fiorenzani for his [ROS 1 tutorial](https://www.youtube.com/watch?v=We6CQHhhOFo) and [corresponding code](https://github.com/tizianofiorenzani/ros_tutorials/blob/master/opencv/src/find_ball.py) on which this repo is based (code reproduced with permission).

One other thing to be wary of: this is a ROS/ament Python package, which means the launch and config files contained will NOT be linked with the `--symlink-install` command for colcon, and will need to be rebuilt after changes.


## Getting started

A launch file and example parameters are provided.

## Nodes

TODO Document them

## Known issues
- Can't easily detect red due to hue wrap. If you need to detect red robustly you'll need to go in and mess with the HSV filtering.