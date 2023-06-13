# CMake tutorial with git
For each task, the required file to modify is shown as (file to edit). The
default working directory is the project root.

## How to invoke CMake?
I prefer to work in the project root and out-of-source build in a subdirectory
./build. To generate the project bindary tree
```shell script
    cmake -S . -B build
```
and you only need to do this once. To build the project
```shell script
    cmake --build build
```

## Step 1
    1. Set the minimum required version of CMake to be 3.10 (CMakeLists.txt)
    2. Create a project named Tutorial (CMakeLists.txt)
    3. Add an executable called Tutorial to the project (CMakeLists.txt)
    4. Replace `atof(argv[1])` with `std::stod(argv[1])` (tutorial.cxx)
    5. Remove `#include <cstdlib>` (tutorial.cxx)
    6. Set the variable CMAKE_CXX_STANDARD to 11 and the variable CMAKE_CXX_STANDARD_REQUIRED to True (CMakeLists.txt)