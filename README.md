# plane_cam.ros

EN

This ```.sdf``` file has been edited for PX4-Gazebo-ROS simulation. The default model publishes only the GStreamer plugin. The files were modified because we needed a high-quality camera simulation (e.g., for computer vision). Now, you can capture high-quality video. Geotagged configuration for the ROS plugin. The plane_cam is configured to look forward.
Important: After running the following commands, any changes made to the ```worlds``` and ```models``` folders will be lost, and the system will revert to its default state.

```
cd ~/PX4-Autopilot/

make clean
  
make distclean
```
Navigate to the models directory:

```
cd ~/PX4-Autopilot/Tools/simulation/gazebo-classic/sitl_gazebo-classic/models/
```
Replace the ```geotagged_cam.sdf``` file with the modified one:
```
cd geotagged_cam/
```



Replace the ```plane_cam.sdf``` file with the modified one:
```
cd ..
cd plane_cam/
```


Compile and run the PX4 simulation:
```
cd ~/PX4-Autopilot
make px4_sitl gazebo-classic_plane_cam
```
Now, you need to use ROS to utilize the camera plugin. (Tested on ROS Noetic). You must use a launch file for this.

```
cd ~/PX4-Autopilot/launch/
nano mavros_posix_sitl.launch
```
Modify the ```iris``` model to ```plane_cam```, then save the file by pressing ```Ctrl+X```, ```Y```, and ```Enter```.

Run the launch file:
```
roslaunch px4 mavros_posix_sitl.launch
```
Open a new terminal and start the image viewer:
```
rosrun rqt_image_view rqt_image_view
```



