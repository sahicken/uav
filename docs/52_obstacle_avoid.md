# Obstacle Avoidance

[check out its github](https://github.com/PX4/PX4-Avoidance/tree/master)

We will need to figure out a way to commuicate a 3D Point Cloud (i.e. [sensor_msgs::PointCloud2](https://docs.ros.org/en/melodic/api/sensor_msgs/html/msg/PointCloud2.html)) utilizing our sensors (a wide angle camera) and ROS nodes. One idea is [Rviz](http://wiki.ros.org/rviz/DisplayTypes/Camera). On their site you can [search nodes](https://index.ros.org/).

## ROS2 XRCE-DDS BRIDGE PX4

We will need to connect the PX4 to our raspberry pi running ROS. Work should be started on simulating PX4 on our raspberry pi and communicating over the bridge. A significant portion of club resources should be delegated to research a solution to the problem described in the above section.