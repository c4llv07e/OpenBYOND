###################################
## OpenBYOND Core Library
###################################

## Project Setup
cmake_minimum_required(VERSION 3.10)

## WHAT A CREATIVE NAME WOW
project(${CMAKE_PROJECT_NAME}-tools)

## Versioning shit
set(VERSION_MAJOR 0)
set(VERSION_MINOR 0)
set(VERSION_PATCH 1)


## Configurations
#message("[OpenBYOND Core] Writing config.h to ${CMAKE_CURRENT_BINARY_DIR}")
#configure_file(config.h.in ${CMAKE_CURRENT_BINARY_DIR}/config.h)

# Add the include folder to the include path
include_directories(
        ${CMAKE_CURRENT_BINARY_DIR}/../openbyond-core/include # I am very sorry
	${OPENBYOND_CORE_INCLUDE_DIR}
	${TCLAP_INCLUDE_DIR}
	)

# Set the source files, headers, and link libraries
##################
# DM PARSER
##################
set(TARGET_NAME "dm")
project(dm)
set(PARSER_SOURCE
	${CMAKE_CURRENT_SOURCE_DIR}/src/dm.cpp
	)

SOURCE_GROUP("src\\parser" FILES ${PARSER_SOURCE})

# Compile the library
add_executable(${TARGET_NAME}
	${OPENBYOND_CORE_INCLUDE}
	${PARSER_SOURCE}
)
target_link_libraries(${TARGET_NAME} openbyond-core)
