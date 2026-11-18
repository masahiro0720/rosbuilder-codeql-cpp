cmake_minimum_required(VERSION 3.8)
project(eval1_minimal_cpp_pkg_interfaces)

find_package(ament_cmake REQUIRED)

# Enable rosidl generation after adding custom interfaces.
# find_package(rosidl_default_generators REQUIRED)
# ament_export_dependencies(rosidl_default_runtime)

install(DIRECTORY msg srv action DESTINATION share/${PROJECT_NAME})
install(
  FILES
    "${CMAKE_CURRENT_SOURCE_DIR}/../LICENSE"
    "${CMAKE_CURRENT_SOURCE_DIR}/../README.md"
  DESTINATION share/${PROJECT_NAME}
)

ament_package()
