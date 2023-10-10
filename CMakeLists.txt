# Set the minimum required version of CMake
cmake_minimum_required(VERSION 3.11)

# Set the project name and version
project(uWebSockets_CAPI VERSION 0.1)

# Use FetchContent to download the uWebSockets repository
include(FetchContent)
FetchContent_Declare(
  uWebSockets
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG main # or use a specific commit hash or tag
)

# Populate the content at configure time
FetchContent_MakeAvailable(uWebSockets)

# Add an alias target for the uWebSockets C API library
add_library(uWebSockets_CAPI INTERFACE)
add_library(uWebSockets_CAPI::uWebSockets_CAPI ALIAS uWebSockets_CAPI)
target_link_libraries(uWebSockets_CAPI INTERFACE uWS::uWS)

# Install the target and its headers
install(TARGETS uWebSockets_CAPI EXPORT uWebSockets_CAPITargets)
install(DIRECTORY ${uWebSockets_SOURCE_DIR}/capi/include/ DESTINATION include/uWebSockets)

# Generate and install the config and version files
include(CMakePackageConfigHelpers)
write_basic_package_version_file(
  uWebSockets_CAPIConfigVersion.cmake
  VERSION ${PROJECT_VERSION}
  COMPATIBILITY SameMajorVersion
)
install(EXPORT uWebSockets_CAPITargets FILE uWebSockets_CAPITargets.cmake NAMESPACE uWS:: DESTINATION lib/cmake/uWebSockets_CAPI)
install(FILES uWebSockets_CAPIConfig.cmake ${CMAKE_CURRENT_BINARY_DIR}/uWebSockets_CAPIConfigVersion.cmake DESTINATION lib/cmake/uWebSockets_CAPI)
