message(STATUS "TODO: Set cmake version to the output of 'cmake --version'")
cmake_minimum_required(VERSION 3.16)

message(STATUS "TODO: Set the project name and version")
project(
  TEMPLATE_PROJECT
  VERSION 0.1
  LANGUAGES CXX)

# Require out-of-source builds
file(TO_CMAKE_PATH "${PROJECT_BINARY_DIR}/CMakeLists.txt" LOC_PATH)
if(EXISTS "${LOC_PATH}")
  message(
    FATAL_ERROR
      "You cannot build in a source directory (or any directory with a 
      CMakeLists.txt file). Please make a build subdirectory. Feel free to
      remove CMakeCache.txt and CMakeFiles."
  )
endif()

# ##############################################################################
# Build options
# ##############################################################################

# ##############################################################################
# Configure Compiler
# ##############################################################################
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
option(BUILD_SHARED_LIBS "Build using shared libraries" ON)
# Include custom cmake modules
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

########################################################################
# Install directories
########################################################################
# CMake module base path
if (NOT CMAKE_MODULES_DIR)
  set(CMAKE_MODULES_DIR lib/cmake)
endif()

message(STATUS
 "TODO: Once you have set the project name, remember to delete include/TEMPLATE_PROJECT")
message(STATUS 
  "TODO: Replace TEMPLATE_PROJECT with the name of your project in the following variables")
set(TEMPLATE_PROJECT_INCLUDE_DIR include/${CMAKE_PROJECT_NAME})
set(TEMPLATE_PROJECT_LIB_DIR     lib)
set(TEMPLATE_PROJECT_CMAKE_DIR   ${CMAKE_MODULES_DIR}/${CMAKE_PROJECT_NAME})
########################################################################
# Find build dependencies
########################################################################
# Use find_package to locate any dependencies

########################################################################
# Create uninstall target
########################################################################
configure_file(
    ${CMAKE_SOURCE_DIR}/cmake/cmake_uninstall.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake
@ONLY)

add_custom_target(uninstall
    ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake
    )

# ##############################################################################
# Add subdirectories
# ##############################################################################
add_subdirectory(include/${PROJECT_NAME})
add_subdirectory(lib)

########################################################################
# Install cmake search helper for this library
########################################################################
message(STATUS "TODO: Also change the TEMPLATE_PROJECT_CMAKE_DIR variable below")
install(FILES cmake/${CMAKE_PROJECT_NAME}_config.cmake
    DESTINATION ${TEMPLATE_PROJECT_CMAKE_DIR}
)