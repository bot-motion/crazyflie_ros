cmake_minimum_required(VERSION 3.5)
project(crazyflie_demo)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

find_package(rclcpp REQUIRED)
find_package(ament_cmake REQUIRED)

set(INCLUDE_DIRS ${rclcpp_INCLUDE_DIRS} ${ament_cmake_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${rclcpp_LIBRARY_DIRS} ${ament_cmake_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${rclcpp_LIBRARIES} ${ament_cmake_LIBRARIES})



# Declare a cpp executable
add_executable(quadrotor_teleop src/quadrotor_teleop.cpp)

# Specify libraries to link a library or executable target against
target_link_libraries(quadrotor_teleop ${LIBS})

ament_export_dependencies(rclcpp)
ament_export_dependencies(ament_cmake)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()

