# gps_pkg
Final Project for ENGR 339 (ROS)


Used Hardware:
Cresent A1000

Connection of Hardware:
The GPS is connected using standard USB connection. The hardware shows up as /dev/ttyUSB0

Source of the scripts:
http://wiki.ros.org/nmea_navsat_driver

This package has following dependency
  geometry_msgs
  nmea_msgs
  python-serial
  roslint
  rospy
  sensor_msgs
  
Permission needed to be granted as following:
> sudo chmod 777 /dev/ttyUSB0

Output of the program:
The program publishes the output in the topic /fix in **nmea_msgs** format

**Gpgga**
# Message from GPGGA NMEA String
Header header

string message_id

# UTC seconds from midnight
float64 utc_seconds

float64 lat
float64 lon

string lat_dir
string lon_dir

uint32 gps_qual

uint32 num_sats
float32 hdop 
float32 alt
string altitude_units

float32 undulation
string undulation_units
uint32 diff_age
string station_id


**Gpgsa**
# Message from GPGSA NMEA String
Header header

string message_id

string auto_manual_mode
uint8 fix_mode

uint8[] sv_ids

float32 pdop
float32 hdop
float32 vdop


**Gpgsv**
# Total number of satellites in view and data about satellites
# Because the NMEA sentence is limited to 4 satellites per message, several
# of these messages may need to be synthesized to get data about all visible
# satellites.

Header header

string message_id

# Number of messages in this sequence
uint8 n_msgs
# This messages number in its sequence. The first message is number 1.
uint8 msg_number

# Number of satellites currently visible
uint8 n_satellites

# Up to 4 satellites are described in each message
GpgsvSatellite[] satellites

**GpgsvSatellite**
# Satellite data structure used in GPGSV messages

# PRN number of the satellite
# GPS = 1..32
# SBAS = 33..64
# GLO = 65..96
uint8 prn

# Elevation, degrees. Maximum 90
uint8 elevation

# Azimuth, True North degrees. [0, 359]
uint16 azimuth

# Signal to noise ratio, 0-99 dB. -1 when null in NMEA sentence (not tracking)
int8 snr



**Gprmc**
# Message from GPRMC NMEA String
Header header

string message_id

float64 utc_seconds
string position_status

float64 lat
float64 lon

string lat_dir
string lon_dir

float32 speed
float32 track
string date
float32 mag_var
string mag_var_direction
string mode_indicator


**Sentence*
# A message representing a single NMEA0183 sentence.

# header.stamp is the ROS Time when the sentence was read.
# header.frame_id is the frame of reference reported by the satellite
#        receiver, usually the location of the antenna.  This is a
#        Euclidean frame relative to the vehicle, not a reference
#        ellipsoid.
Header header

# This should only contain ASCII characters in order to be a valid NMEA0183 sentence.
string sentence

Expected error and required steps to solve them:
The GPS outputs msgs in different baud rate. We can change the baud rate as the parameter in the launch file.
