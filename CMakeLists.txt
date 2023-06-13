cmake_minimum_required(VERSION 3.10)

project(Tutorial VERSION 1.0)

# specify the required C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# add configure file to modify information like version in source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# the main target
add_executable(Tutorial tutorial.cxx)

# add binary build tree to include directory which the compiler will search
target_include_directories(Tutorial PUBLIC
                           ${PROJECT_BINARY_DIR}
                           )