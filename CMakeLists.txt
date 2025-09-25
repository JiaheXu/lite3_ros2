cmake_minimum_required(VERSION 3.8)
project(lite3_ros2)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(tf2 REQUIRED)
find_package(tf2_ros REQUIRED)


include_directories(
  include
)

# Nodes



add_executable(qnx2ros src/qnx2ros.cpp)
ament_target_dependencies(qnx2ros rclcpp std_msgs sensor_msgs geometry_msgs nav_msgs tf2 tf2_ros)


#add_executable(sensor_checker src/sensor_checker.cpp)
#ament_target_dependencies(sensor_checker rclcpp std_msgs sensor_msgs geometry_msgs nav_msgs tf2 tf2_ros)

# Install
install(TARGETS  qnx2ros  #sensor_checker
  DESTINATION lib/${PROJECT_NAME}
)

install(DIRECTORY include/
  DESTINATION include/
)

ament_package()
