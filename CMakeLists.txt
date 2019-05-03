cmake_minimum_required(VERSION 2.8.3)
project(nmea_navsat_driver)		project(gps_pkg)
find_package(catkin REQUIRED)		find_package(catkin REQUIRED)
catkin_python_setup()		catkin_python_setup()
catkin_package()		catkin_package()
install(PROGRAMS		install(PROGRAMS
   scripts/nmea_serial_driver		   scripts/nmea_serial_driver
   scripts/nmea_socket_driver		   scripts/nmea_socket_driver
   scripts/nmea_topic_driver		   scripts/nmea_topic_driver
   scripts/nmea_topic_serial_reader		   scripts/nmea_topic_serial_reader
   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}		   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)		)
install(DIRECTORY launch/		install(DIRECTORY launch/
   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch		   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
   FILES_MATCHING PATTERN "*.launch"		   FILES_MATCHING PATTERN "*.launch"
)		)
if (CATKIN_ENABLE_TESTING)		if (CATKIN_ENABLE_TESTING)
  find_package(roslint)		  find_package(roslint)
  roslint_python()		  roslint_python()
  roslint_add_test()		  roslint_add_test()
endif()		endif()
