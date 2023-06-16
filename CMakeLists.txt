cmake_minimum_required(VERSION 3.10)

project(Tutorial VERSION 1.0)

# specify the required C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# add configure file to modify information like version in source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# before build the main target, we must build the library first
# here we use a relative path and it is evaluated with respect to
# current path. This subdirectory must have a CMakeLists.txt
add_subdirectory(MathFunctions)

# the main target
add_executable(Tutorial tutorial.cxx)

# link our library (MathFunctions) to our executable (Tutorial)
# I don't know what PUBLIC means right now.
target_link_libraries(Tutorial PUBLIC MathFunctions)

# add binary build tree to include directory which the compiler will search
# why do we need to use quotes?
target_include_directories(Tutorial PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           "${PROJECT_SOURCE_DIR}/MathFunctions"
                           )