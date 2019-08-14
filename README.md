# RTAB-Map using Intel RealSense D435
This package **reconfig param of rtabmap_ros for realsense camera**. [rtabmap_ros](https://github.com/introlab/rtabmap_ros) is build by [IntRoLab](https://github.com/introlab). <br>
This package config all parmeter for SLAM using RealSense D435 Camera.
## 1. Installation
1.0. Install realsense2_camera for Ubuntu <br>
1.1. Build Rtabmap (Kinetic version) <br>
* Install dependence
```
$ sudo apt install ros-kinetic-rtabmap
$ sudo apt install ros-kinetic-rtabmap-ros
```
* Install RTAB-Map library
```
$ cd ~
$ git clone https://github.com/introlab/rtabmap.git rtabmap
$ cd rtabmap/build
$ cmake .. 
$ make
$ sudo make install
```
* Install rtabmap_ros_realsense (all parameters for RealSense Camera) or [rtabmap_ros](https://github.com/introlab/rtabmap_ros) of IntRoLab
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/DuyNamUET/rtabmap_ros_realsense.git
$ cd ..
$ catkin_make
```
1.2. Build from source for NVIDIA Jetson <br>
## 2. Mapping and Localization
2.1. Connect RenSense D435 Camera 
* RGB-D handheld mapping
```
$ roslaunch realsense2_camera rs_aligned_depth.launch
```
* Using bag file
```
$ roslaucnh realsense2_camera rs_from_file.launch aligned_depth:=true rosbag_filename:=path/to/bag/file.bag
```
2.2. Mapping
```
$ roslaunch rtabmap_ros_realsense realsense_mapping.launch
```
2.3. Localization
After mapping, we have database in ~/catkin_ws/src/data/rtabmap.db (default)
```
$ roslaunch rtabmap_ros_realsense realsense_localization.launch
```