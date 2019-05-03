# gps_pkg
Final Project for ENGR 339 (ROS)


**Used Hardware:**  
Cresent A1000

**Connection of Hardware:**  
The GPS is connected using standard USB connection. The hardware shows up as /dev/ttyUSB0

**Source of the scripts:**  
http://wiki.ros.org/nmea_navsat_driver

**This package has following dependency:**  
  geometry_msgs  
  nmea_msgs  
  python-serial  
  roslint  
  rospy  
  sensor_msgs  
  
**Permission needed to be granted as following:**  
> sudo chmod 777 /dev/ttyUSB0  
  
**Output of the program:**  
The program publishes the output in the topic /fix in **nmea_msgs** format  
  
*Gpgga* 
http://docs.ros.org/api/nmea_msgs/html/msg/Gpgga.html


*Gpgsa*
http://docs.ros.org/api/nmea_msgs/html/msg/Gpgsa.html


*Gpgsv*
http://docs.ros.org/api/nmea_msgs/html/msg/Gpgsv.html

*GpgsvSatellite*
http://docs.ros.org/api/nmea_msgs/html/msg/GpgsvSatellite.html

*Gprmc*
http://docs.ros.org/api/nmea_msgs/html/msg/Gprmc.html


*Sentence*
http://docs.ros.org/api/nmea_msgs/html/msg/Sentence.html


**Expected error and required steps to solve them:**  
The GPS outputs msgs in different baud rate. We can change the baud rate as the parameter in the launch file.
