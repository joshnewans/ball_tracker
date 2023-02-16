# ball_tracker

This repository contains a simple demonstration of using ROS and OpenCV to track a ball with a mobile robot via a camera feed.

The associated tutorial is available [here](https://youtu.be/gISSSbYUZag).

Note that at present this repository will **not** work. There is a key script (`ball_tracker/process_image.py`) missing which cannot be distributed as it borrows heavily from [this file](https://github.com/tizianofiorenzani/ros_tutorials/blob/master/opencv/src/find_ball.py) which is not licensed for derivative works.

In the future if permission is obtained or I rewrite the required functions from scratch, I will update this repo.

One other thing to be wary of: this is a ROS/ament Python package, which means the launch and config files contained will be linked with the `--symlink-install` command for colcon, and will need to be rebuilt after changes.


## Getting started

A launch file and example parameters are provided.

## Nodes

TODO Document them

## Known issues
- Can't easily detect red due to hue wrap. If you need to detect red robustly you'll need to go in and mess with the HSV filtering.