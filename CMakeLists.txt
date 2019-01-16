cmake_minimum_required(VERSION 3.2.1)
PROJECT(testVCS3)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/"

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

message("---------------- DIR : $ENV{SHINE_BASE_DIR}")
find_package(ShSDK REQUIRED StubUserSystem ShEntryPoint ${USE_MODULE})

# Enable C++11
set(CMAKE_CXX_STANDARD 11)

# Warnings
if (MSVC)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_CRT_SECURE_NO_WARNINGS")
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_SCL_SECURE_NO_WARNINGS") # use /wd4996 instead ?
else (MSVC)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra")
endif (MSVC)

# Set some additionnal compile flags
INCLUDE(cmake/Modules/Master.cmake)
INCLUDE(cmake/TargetBuildSAAS.cmake)

ConfigureShineSAAS()

add_subdirectory(/home/lcausin/tmp//src)

