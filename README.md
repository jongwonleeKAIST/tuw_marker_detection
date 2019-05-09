# tuw_visual_marker
This is a ros package collection to detect visual markers.
It contains a node to detect artags, ellipses and a camera library optimized for Logitech cameras.

# tuw_uvc
## Dependencies
```
sudo apt-get install libv4l-dev
sudo apt-get install libsdl1.2-dev
```

# How to use
1. First, run a camera. For our objective, the comment is:
```
roslaunch realsense2_camera rs_aligned_depth.launch
```

2. Prepare a 8 x 6 3cm checkerboard to calibrate the camera. The pattern is at the directory:
```
${PACKAGE_DIR}/tuw_marker_detection/tuw_checkerboard/pattern/checkerboard8x6.pdf
```
Please be aware that the pattern is printed in a real size.

3. Run a launch file.
```
roslaunch tuw_checkerboard demo.launch
```
Then, a rviz and an image window will be appeared with an imaginary 3D axis.

4. According to the axis's position with respect to the origin of a world coordinate, re-tune ros parameters. They can be adjusted by executing
```
rosrun rqt_reconfigure rqt_reconfigure
```
Please be aware that 'x_boardtobase' and 'y_boardtobase' denotes relative position from the imaginary axis and the origin of a base coordinate.


* To proceed the procedure bellow, please refer to the package ball_detection that I have uploaded.

5. Print out rotation and translation matrix between two coordinates on a terminal. It can be achieved by:
```
rosrun ball_detection tf_listener
```

6. Copy and paste those two arrays on two variables 'float rotation[9]' and 'translation[3]' at ball_detection/ball_detect.h
