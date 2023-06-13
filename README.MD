# CMake tutorial with git
For each task, the required file to modify is shown as (file to edit). The
default working directory is the project root.

## How to invoke CMake?
I prefer to work in the project root and out-of-source build in a subdirectory
./build. To generate the project binary build tree
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
4. Replace 'atof(argv[1])' with 'std::stod(argv[1])' (tutorial.cxx)
5. Remove '#include <cstdlib>' (tutorial.cxx)
6. Set the variable CMAKE_CXX_STANDARD to 11 and the variable CMAKE_CXX_STANDARD_REQUIRED to True (CMakeLists.txt)
7.  Set the project version number as 1.0 in the project command (CMakeLists.txt)
8.  Use configure_file to configure and copy TutorialConfig.h.in to TutorialConfig.h (CMakeLists.txt)
9.  Use target_include_directories to include ${PROJECT_BINARY_DIR} (CMakeLists.txt)
10. Define Tutorial_VERSION_MAJOR and Tutorial_VERSION_MINOR (TutorialConfig.h.in)
11. Include TutorialConfig.h (tutorial.cxx)
12. Create a print statement using Tutorial_VERSION_MAJOR and Tutorial_VERSION_MINO (tutorial.cxx)

Remarks
- The basic usage of configure_file is
```
configure_file(<input> <output>)
```
where default paths are CMAKE_CURRENT_SOURCE_DIR (project root for this exerise) and CMAKE_CURRENT_BINARY_DIR (build directory), respectively.
- fds