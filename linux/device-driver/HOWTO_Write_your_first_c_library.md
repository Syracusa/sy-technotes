# HOWTO : Write your own c library
 - This post will explain how to make your own c library.
 - It's a good idea that make your features with seperated library, not just attach to your main application. This idea reduces your code complexity.

## Table of contents
 0. Make organized directory.
 1. Write your feature.
 2. Make header which will used by library users.
 3. Build library.
 4. Write testapp.
 5. Build testapp and link with your library.
 6. Execute Testapp.


## 0. Make organized directory.
 - The below example shows general directory structure when making library.
 ```
/your-lib
/lib                    ---> Your library's code will go here.
/lib/CmakeLists.txt
/lib/yourlib.c
/include                ---> Header file's that have function declarations which you want to export.
/include/yourlib.h
/apps                   ---> Sample application that users can consult with.
/apps/sample.c
/build                  ---> Build directory that cmake use. Generated binary will goes here.
CmakeLists.txt          ---> Build Script
README.md               ---> The information you wanna tell users.

 ```
## 1. Write your feature
- This library has one simple function that prints some text when called.
```
/* yourlib/lib/yourlib.c */
#include <stdio.h>
void yourlib_test_function()
{
    printf("Test function called\n");
}
```


## 2. Make header which will used by library users
```
/* yourlib/include/yourlib.h */
#ifndef YOURLIB_H
#define YOURLIB_H

void yourlib_test_function();

#endif
```


## 3. Build library
 - We will use cmake for build this library.
 - yourlib/CMakeLists.txt
```
cmake_minimum_required(VERSION 3.10)
project(yourlib
        VERSION 1.0
        DESCRIPTION "Your test library"
        LANGUAGES C)
              
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fsanitize=address")

add_subdirectory(lib)
```

 - yourlib/lib/CMakeLists.txt
add_library(yourlib yourlib.c)

target_include_directories(yourlib PUBLIC
                          "${PROJECT_BINARY_DIR}"
                          "${PROJECT_SOURCE_DIR}/lib/"
                          ) 


 - Commands to build
```
#!bin/bash
cd build
cmake ..
make
```

## 4. Write testapp
```
/* yourlib/apps/sample.c */
#include "yourlib.h"

int main()
{
    printf("Testapp main\n");
    yourlib_test_function();
}
```

## 5. Build testapp and link with your library

 - yourlib/CMakeLists.txt (Append)
```
add_subdirectory(apps)
```

- yourlib/apps/CMakeLists.txt
```
add_executable(sample sample.c)
target_link_libraries(sample yourlib)
target_include_directories(sample PUBLIC "${PROJECT_SOURCE_DIR}/include")
```

- Test app build commands

```
#!bin/bash
cd build
cmake ..
make
```

## 6. Execute Testapp

```
#!bin/bash
cd build
./sample
```