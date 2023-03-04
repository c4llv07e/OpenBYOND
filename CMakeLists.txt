##########################################
## OpenBYOND - Compile Script
##########################################

cmake_minimum_required(VERSION 3.10)

## WHAT A CREATIVE NAME WOW
project(openbyond)

## Versioning shit
set(VERSION_MAJOR 0)
set(VERSION_MINOR 0)
set(VERSION_PATCH 1)

# Uncomment the line below to set the build type
# set(CMAKE_BUILD_TYPE DEBUG)

# Extend the find_package search path
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH    ${CMAKE_SOURCE_DIR}/bin)

# Find Allegro
find_package(allegro 5.0 REQUIRED COMPONENTS
  main font ttf native_dialog primitives tiled
)

# Find TCLAP
find_package(TCLAP REQUIRED)

#include_directories(${allegro_INCLUDE_DIRS})
#list(APPEND ${PROJECT_NAME}_LINK_LIBS ${allegro_LIBRARIES})

include(CheckFunctionExists)
CHECK_FUNCTION_EXISTS("vasprintf" HAVE_VASPRINTF)

if(CMAKE_COMPILER_IS_GNUCXX)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()


#
# Every module has a CMakeLists.txt in it's root. 
add_subdirectory(openbyond-core)
include_directories(openbyond-core/include)
add_subdirectory(openbyond-tools)
add_subdirectory(openbyond-server)
add_subdirectory(openbyond-client)
add_subdirectory(openbyond-ide)
