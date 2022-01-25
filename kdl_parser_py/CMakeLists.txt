cmake_minimum_required(VERSION 3.5)

project(kdl_parser_py)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(ros_testing REQUIRED)

set(INCLUDE_DIRS ${ament_cmake_INCLUDE_DIRS} ${rostest_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS} ${rostest_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES} ${rostest_LIBRARIES})

ament_python_install_package(${PROJECT_NAME})

if(BUILD_TESTING)
  add_ros_test(test/test_kdl_parser.launch)
endif()

ament_export_dependencies(ament_cmake)
ament_export_dependencies(rostest)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
