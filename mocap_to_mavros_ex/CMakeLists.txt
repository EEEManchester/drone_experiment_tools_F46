cmake_minimum_required(VERSION 3.0.2)
project(mocap_to_mavros_ex)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  mavros
  roscpp
  std_msgs
  vicon_bridge
)

find_package(Eigen3 3.3 REQUIRED NO_MODULE)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES mocap_to_mavros_ex
#  CATKIN_DEPENDS geometry_msgs mavros roscpp std_msgs vicon_bridge
#  DEPENDS system_lib
)

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

add_executable(mocap_to_drone_node src/mocap_to_drone_node.cpp)

target_link_libraries(mocap_to_drone_node
  ${catkin_LIBRARIES}
)

add_executable(mocap_to_drone_node_NED src/mocap_to_drone_node_NED.cpp)

target_link_libraries(mocap_to_drone_node_NED
  ${catkin_LIBRARIES}
  Eigen3::Eigen
)
