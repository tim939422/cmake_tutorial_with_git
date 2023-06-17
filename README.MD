# CMake tutorial with git
For each task, the required file to modify is shown as (file to edit). The
default working directory is the project root.
cmake version 3.26

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
If you want to turn off an option
```shell script
cmake -S . -B build -DUSE_MYMATH=OFF
```
-D<option>=OFF/ON

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

## Step 2
1. Add a library called MathFunctions (MathFunctions/CMakeLists.txt) Hint: You will need the add_library command
2. Use add_subdirectory() to add MathFunctions to this project (CMakeLists.txt)
3. Use target_link_libraries to link the library to our executable (CMakeLists.txt)
4. Add MathFunctions to Tutorial's target_include_directories() (CMakeLists.txt)
5. Include MathFunctions.h (tutorial.cxx)
6. Replace sqrt with mysqrt (tutorial.cxx)
7. Create a variable USE_MYMATH using option and set default to ON (CMakeLists.txt)
8. Use list() and APPEND to create a list of optional libraries called EXTRA_LIBS and a list of optional include directories called EXTRA_INCLUDES. Add the MathFunctions library and source directory to the appropriate lists. (CMakeLists.txt)
9. Use EXTRA_LIBS instead of the MathFunctions specific values in target_link_libraries. (CMakeLists.txt)
10. Use EXTRA_INCLUDES instead of the MathFunctions specific values in target_include_directories. (CMakeLists.txt)
11. Only include MathFunctions if USE_MYMATH is defined (tutorial.cxx)
12. Use mysqrt if USE_MYMATH is defined and sqrt otherwise (tutorial.cxx)
13. use cmakedefine to define USE_MYMATH (TutorialConfig.h.in)

## Step 3
1. State that anybody linking to MathFunctions needs to include the current source directory, while MathFunctions itself doesn't. (Hint: Use target_include_directories with the INTERFACE keyword) (MathFunctions/CMakeLists.txt)
2. Remove EXTRA_INCLUDES list (CMakeLists.txt)
3. Remove use of EXTRA_INCLUDES (CMakeLists.txt)