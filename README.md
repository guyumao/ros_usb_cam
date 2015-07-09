# ros_usb_cam
使用说明没有源码.....
https://github.com/bosch-ros-pkg/usb_cam 为usb的现在还在维护的库
git到在catkin下的src下，然后catkin_make  使其以使用。
 编写usb_cam.launch文件：
  
<launch>
  <node name="usb_cam" pkg="usb_cam" type="usb_cam_node" output="screen" >
    <param name="video_device" value="/dev/video0" />
    <param name="image_width" value="640" />
    <param name="image_height" value="480" />
     <param name="framerate" value="30" />
    <param name="pixel_format" value="mjpeg" />
    <param name="camera_frame_id" value="usb_cam" />
    <param name="io_method" value="mmap"/>
  </node>
  <node name="image_view" pkg="image_view" type="image_view" respawn="false" output="screen">
    <remap from="image" to="/usb_cam/image_raw"/>
    <param name="autosize" value="true" />
  </node>
</launch>
mjpeg类型和yuyv类型，若出现"Webcam: expected picture but didn't get it..."请考虑修改类型pixel_format参数

有关的几个链接http://wiki.ros.org/Sensors/Cameras
http://wiki.ros.org/image_transport/Tutorials/PublishingImages
http://wiki.ros.org/usb_cam
