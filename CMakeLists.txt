cmake_minimum_required(VERSION 3.10)

project(Tutorial)

# specify the required C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable(Tutorial tutorial.cxx)
