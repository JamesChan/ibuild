cmake_minimum_required(VERSION 2.8.3)

project(hello)

set(IBUILD_ROOT ${CMAKE_CURRENT_SOURCE_DIR}/../)

set(CMAKE_MODULE_PATH 
	${CMAKE_MODULE_PATH}
	"${CMAKE_CURRENT_SOURCE_DIR}/cmake"
	"${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules"
	"${IBUILD_ROOT}/cmake/modules")

include(assert)
include(tests)
set(GTEST_SOURCE_SEARCHING_DIR ${CMAKE_SOURCE_DIR}/../../tools)
include(gtest)

add_library(libsample4 sample4.cc)
catkin_add_gtest(hello-utest sample4_unittest.cc WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

target_link_libraries(hello-utest libsample4)

