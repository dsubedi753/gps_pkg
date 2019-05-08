# Final Project for ENGR 339 (ROS)
# gps_pkg


**Used Hardware:**  
Cresent A1000  
https://hemispheregnss.com/Portals/0/TechnicalDocumentation/A100_User_Guide_8750163000_RevC1.pdf

**Installation:**  
The Cresent A1000 need 12V DC supply for the operation. The hardware is connected using standard USB connection. The hardware shows up as /dev/ttyUSB0.

**Source of the scripts:**  
http://wiki.ros.org/nmea_navsat_driver

**This package has following dependency:**  
  geometry_msgs  
  nmea_msgs  
  python-serial  
  roslint  
  rospy  
  sensor_msgs  
  
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
The GPS outputs msgs in different and discrete baud rate. If the input baud rate at which the script is executed doesn't match the baud rate of the hardware, the program outputs nothing or erroneous information. We can change the baud rate as the parameter in the launch file.

The package will not output the data if the harware is not given the correct permission. We can used following command to specify the permission to access the hardware. 

**Command to grant the Permission:**  
> sudo chmod 777 /dev/ttyUSB0  

**Running the package**  
Open Terminal  
Type in the following code  
> roslaunch gps_pkg gps.launch
