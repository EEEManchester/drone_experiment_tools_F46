cmake_minimum_required(VERSION 3.0.2)
project(drone_offboard_ex)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  mavros
  roscpp
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES drone_offboard_example
#  CATKIN_DEPENDS geometry_msgs mavros roscapp
#  DEPENDS system_lib
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)


add_executable(drone_offboard_node src/off_board.cpp)

target_link_libraries(
	drone_offboard_node
	${catkin_LIBRARIES}
	)


add_executable(drone_offboard_raw_node src/off_board_raw.cpp)

target_link_libraries(
	drone_offboard_raw_node
	${catkin_LIBRARIES}
	)
