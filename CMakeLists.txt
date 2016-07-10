#
# author    : huang li long <huanglilongwk@outlook.com>
# time      : 2016/07/10
# brief     : port makefile project to cmake project 
# ref	    : https://github.com/mavlink/c_uart_interface_example
#

cmake_minimum_required(VERSION 3.2)

# project name
project(uart_interface)

# mavlink header files directory
set(MAVLINK_DIR c_library_v1)

# include header file's directory path
include_directories(${PROJECT_SOURCE_DIR}
		    ${PROJECT_SOURCE_DIR}/serial_port
                    ${MAVLINK_DIR})

# create library 
add_subdirectory(serial_port)

# create executable 
add_executable(uart_interface mavlink_control.cpp)

# link library 
target_link_libraries(uart_interface serial_port pthread)
