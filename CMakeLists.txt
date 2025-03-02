cmake_minimum_required(VERSION 3.22)

set (PKG_NAME cpp_template_pkg)
set (MAIN_EXECUTABLE_NAME main)

project(${PKG_NAME})
cmake_policy(SET CMP0079 NEW)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_ros REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_subdirectory(libraries) # Add this line to include the libraries directory

install(
  DIRECTORY include/
  DESTINATION include
)

add_executable(${MAIN_EXECUTABLE_NAME} src/main.cpp) # Create the talker executable

target_include_directories(${MAIN_EXECUTABLE_NAME} PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

LibraryLinker(${MAIN_EXECUTABLE_NAME})

install(TARGETS ${MAIN_EXECUTABLE_NAME}
  DESTINATION lib/${PROJECT_NAME}
)

ament_export_include_directories(
  include
)

ament_export_targets(
  export_${PROJECT_NAME}
)

ament_package()
