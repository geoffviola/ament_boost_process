cmake_minimum_required(VERSION 3.5)
project(ament_boost_process)

find_package(ament_cmake REQUIRED)
find_package(ament_boost REQUIRED)

add_custom_target(update_subrepo ALL
  git submodule update --init --recursive
  WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}")

install(
  DIRECTORY "${CMAKE_SOURCE_DIR}/src/boost_process/include/boost"
  DESTINATION include
  MESSAGE_NEVER)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
