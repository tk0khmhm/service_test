cmake_minimum_required(VERSION 2.8.3)
project(service_test)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs	# dependencies of srv
  message_generation	# for generation srv, msg
)


## Generate services in the 'srv' folder
add_service_files(
  FILES
  AddTwoInts.srv	# srv file to generate
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs  # Or other packages containing msgs
)
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES service_test
#  CATKIN_DEPENDS roscpp rospy
#  DEPENDS system_lib
)

###########
## Build ##
###########

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(add_two_ints_server src/add_two_ints_server.cpp)
target_link_libraries(add_two_ints_server
  ${catkin_LIBRARIES}
)

add_executable(add_two_ints_client src/add_two_ints_client.cpp)
target_link_libraries(add_two_ints_client
  ${catkin_LIBRARIES}
)

