cmake_minimum_required(VERSION 3.8)
project(DrAss_cpp)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(Input_pub src/Input_pub.cpp)
ament_target_dependencies(Input_pub rclcpp std_msgs)
add_executable(IMU_pub src/IMU_pub.cpp)
ament_target_dependencies(IMU_pub rclcpp std_msgs)
add_executable(Hall_pub src/Hall_pub.cpp)
ament_target_dependencies(Hall_pub rclcpp std_msgs)


install(TARGETS
  Input_pub
  IMU_pub
  Hall_pub
  DESTINATION lib/${PROJECT_NAME})

ament_package()
