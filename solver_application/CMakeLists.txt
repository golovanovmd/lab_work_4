cmake_minimum_required(VERSION 3.4)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(solver)

add_library(formatter STATIC ${CMAKE_CURRENT_SOURCE_DIR}/../formatter/formatter.cpp)
add_library(formatter_ex STATIC ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex/formatter_ex.cpp)
add_library(solver STATIC ${CMAKE_CURRENT_SOURCE_DIR}/../solver/solver.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../solver)

target_link_libraries(formatter_ex formatter)
add_executable(equation ${CMAKE_CURRENT_SOURCE_DIR}/equation.cpp)
target_link_libraries(equation formatter_ex solver)