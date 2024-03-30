# https://stackoverflow.com/questions/6352123/multiple-directories-under-cmake

cmake_minimum_required(VERSION 3.0.0)
project(strtt VERSION 0.2.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)

# build libusb library
add_subdirectory(src/libusb)

set(LIBUSB_INCLUDE_DIR src/libusb/libusb/libusb)
set(LIBUSB_LIBRARY ${CMAKE_BINARY_DIR}/src/libusb/libusb-1.0.a)
include_directories(${LIBUSB_INCLUDE_DIR})

# build stlink library
add_subdirectory(src/openocd)

# build sample app
add_subdirectory(src/rtt)