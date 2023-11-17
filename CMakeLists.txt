cmake_minimum_required(VERSION 3.4...3.18)
project(cmake_example)

set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g")

add_library(mymath STATIC src/mymath.cpp)
set_target_properties(mymath PROPERTIES POSITION_INDEPENDENT_CODE ON)

add_subdirectory(pybind11)
pybind11_add_module(cmake_example src/binder.cpp)
target_link_libraries(cmake_example PRIVATE mymath)
