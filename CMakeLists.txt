cmake_minimum_required(VERSION 3.13.4)

project(DVGUI VERSION 0.1.0 DESCRIPTION "Deep Vecrtic GUI is the second edition of the mfGUI.")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

set(CMAKE_CXX_STANDARD 17)

add_library(${PROJECT_NAME} STATIC)

##FILES##
file(GLOB_RECURSE sources src/*.cpp src/*.hpp)
#########

target_sources(${PROJECT_NAME} PRIVATE ${sources})

target_include_directories(${PROJECT_NAME}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

set_target_properties(${PROJECT_NAME} PROPERTIES DEBUG_POSTFIX "d")