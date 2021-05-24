cmake_minimum_required(VERSION 3.0)

project(linenoise)

include(GNUInstallDirs)

option(BUILD_EXAMPLES "Build the examples" ON)

add_library(linenoise INTERFACE)
set_target_properties(linenoise PROPERTIES PUBLIC_HEADER "${CMAKE_CURRENT_SOURCE_DIR}/linenoise.hpp")
target_include_directories(linenoise INTERFACE $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}> INTERFACE $<INSTALL_INTERFACE:${CMAKE_INSTALL_FULL_INCLUDEDIR}>)
install(TARGETS linenoise)

if(BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()
