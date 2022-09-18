cmake_minimum_required(VERSION 3.5)
project(mytool)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)

find_package(geometry_msgs REQUIRED)

find_package(rclcpp REQUIRED)


set(dependencies "geometry_msgs" "rclcpp" )


add_executable(teleop_key src/teleop_turtle_key.cpp)
ament_target_dependencies(teleop_key ${dependencies})


install(TARGETS teleop_key
  DESTINATION lib/${PROJECT_NAME})


ament_package()
