cmake_minimum_required(VERSION 2.8.3)

project(hello)
include(assert.cmake)
include(tests.cmake)
include(gtest.cmake)

add_library(libsample4 sample4.cc)
catkin_add_gtest(hello-utest sample4_unittest.cc WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

target_link_libraries(hello-utest libsample4)

