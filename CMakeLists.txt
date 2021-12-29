cmake_minimum_required(VERSION 3.10)

project(cmake_test)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# set(SPDLOG_BUILD_SHARED ON)
add_subdirectory("${CMAKE_SOURCE_DIR}/spdlog")

file(GLOB_RECURSE SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
# add_library(test STATIC ${SOURCES})
add_library(test SHARED ${SOURCES})
target_include_directories(test PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/src")

target_link_libraries(test PRIVATE spdlog::spdlog)
