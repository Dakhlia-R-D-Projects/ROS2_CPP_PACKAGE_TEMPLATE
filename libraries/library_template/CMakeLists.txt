get_filename_component(LIB_NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME) # Get the name of the library from the directory name in variable LIB_NAME

# Get all .cpp and .hpp files separately
file(GLOB CPP_FILES LIST_DIRECTORIES false "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp") 
file(GLOB HPP_FILES LIST_DIRECTORIES false "${CMAKE_CURRENT_SOURCE_DIR}/*.hpp")

# Create the library dynamically with found .cpp files
add_library(${LIB_NAME} ${CPP_FILES} ${HPP_FILES})

target_compile_features(${LIB_NAME} PUBLIC c_std_99 cxx_std_17)  # Require C99 and C++17

target_include_directories(${LIB_NAME} PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  $<INSTALL_INTERFACE:include>
)

ament_target_dependencies(
  ${LIB_NAME}
  rclcpp
  std_msgs
)

install(
  TARGETS ${LIB_NAME}
  EXPORT export_${PROJECT_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

ament_export_include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}
)

ament_export_libraries(
    ${LIB_NAME}
)

