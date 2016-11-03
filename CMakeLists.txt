cmake_minimum_required(VERSION 3.5)
project(ament_boost_process)

find_package(ament_cmake REQUIRED)
find_package(ament_boost REQUIRED)

configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/git_submodule_update_no_ignore_error.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/git_submodule_update_no_ignore_error.cmake
  COPYONLY
)

add_custom_target(git_boost_subsubmodule_dl ALL
    ${CMAKE_COMMAND} -P
    "${CMAKE_CURRENT_BINARY_DIR}/git_submodule_update_no_ignore_error.cmake")

install(
    DIRECTORY "${CMAKE_SOURCE_DIR}/src/boost_process/include/boost"
    DESTINATION include
    MESSAGE_NEVER)

ament_package()
