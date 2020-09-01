cmake_minimum_required(VERSION 3.8.2)
project(dynamic_view_planning_msgs)

set(CMAKE_CXX_STANDARD 17)

find_package(catkin REQUIRED COMPONENTS 
  geometry_msgs
  roscpp
  sensor_msgs
  std_msgs
  std_srvs
  tf2_sensor_msgs
  ufomap_msgs
  message_generation
  geometry_msgs
)

add_service_files(
  FILES
  ChangeCamera.srv
  AnalyseFile.srv
  RequestIG.srv
)

generate_messages(
  DEPENDENCIES
  geometry_msgs
  std_msgs
  ufomap_msgs
)

catkin_package(
  INCLUDE_DIRS include
  DEPENDS geometry_msgs message_runtime std_msgs
)

install(DIRECTORY include/
  DESTINATION include
  FILES_MATCHING PATTERN "*.h"
  PATTERN ".svn" EXCLUDE
)