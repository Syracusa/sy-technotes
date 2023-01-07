# How to make BBB cross compile environment with cmake
+ Reference
  + https://cmake.org/cmake/help/book/mastering-cmake/chapter/Cross%20Compiling%20With%20CMake.html
  + https://github.com/robamu-org/beaglebone-crosscompiling

+ Assume your CMakeLists.txt file alredy exist
+ Download toolchain
  + https://www.dropbox.com/sh/gn9bo472yalknra/AADrjB6NkMJldaTe4ZzmA-nHa/toolchains?dl=0&subfolder_nav_tracking=1
  + arm-cortex_a8-linux-gnueabihf-debian.tar.gz
+ Extract toolchain at /usr/x-tools
+ Make toolchain file(bbb_toolchain.cmake)
```
# the name of the target operating system
set(CMAKE_SYSTEM_NAME Linux)

# which compilers to use for C
set(CMAKE_C_COMPILER    /usr/x-tools/arm-cortex_a8-linux-gnueabihf-debian/bin/arm-cortex_a8-linux-gnueabihf-gcc)

# where is the target environment located
set(CMAKE_FIND_ROOT_PATH  /usr/x-tools/arm-cortex_a8-linux-gnueabihf-debian/arm-cortex_a8-linux-gnueabihf/sysroot)

# adjust the default behavior of the FIND_XXX() commands:
# search programs in the host environment
set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)

# search headers and libraries in the target environment
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)
```
+ Build with command
```
mkdir -p cbuild
cd cbuild
cmake -DCMAKE_TOOLCHAIN_FILE=../bbb_toolchain.cmake ..
make

```



# Link with static library


# Define git time macro
```
execute_process(COMMAND git log -1 --format=%ad --date=iso8601 WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}" OUTPUT_VARIABLE GIT_DATE ERROR_QUIET OUTPUT_STRIP_TRAILING_WHITESPACE)
message("GIT_DATE:" ${GIT_DATE})
add_definitions(-D__GIT_DATE__="${GIT_DATE}")
```


# CMake with toolchain file
```
cmake -DCMAKE_TOOLCHAIN_FILE=../mytoolchainfile.cmake ..
```

