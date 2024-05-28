cmake_minimum_required(VERSION 3.4)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(hello_world)

add_library(formatter STATIC ${CMAKE_CURRENT_SOURCE_DIR}/../formatter/formatter.cpp)
add_library(formatter_ex STATIC ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex/formatter_ex.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter)

target_link_libraries(formatter_ex formatter)

add_executable(hello_world ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.cpp)
target_link_libraries(hello_world formatter_ex)