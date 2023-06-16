cmake_minimum_required(VERSION 3.10)

project(Tutorial VERSION 1.0)

# specify the required C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# provide options (the same functionality may be from generic implementation
# or mature thirdparty library)
option(USE_MYMATH "Use tutorial provided math implementation" ON)

# add configure file to modify information like version in source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# before build the main target, we must build the library first
# here we use a relative path and it is evaluated with respect to
# current path. This subdirectory must have a CMakeLists.txt
if(USE_MYMATH)
    add_subdirectory(MathFunctions)
    list(APPEND EXTRA_LIBS MathFunctions)
    list(APPEND EXTRA_INCLUDES "${PROJECT_SOURCE_DIR}/MathFunctions")
endif()

# the main target
add_executable(Tutorial tutorial.cxx)

# link our library (MathFunctions) to our executable (Tutorial)
# I don't know what PUBLIC means right now.
target_link_libraries(Tutorial PUBLIC ${EXTRA_LIBS})

# add binary build tree to include directory which the compiler will search
# when do we need to use quotes when use a reference of a variable?
target_include_directories(Tutorial PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           ${EXTRA_INCLUDES}
                           )