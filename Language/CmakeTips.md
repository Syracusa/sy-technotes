
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