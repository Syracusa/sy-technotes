# Undefined reference to 'cap_get_proc'
## Symptom
+ unix-caps.c:(.text+0x1d): undefined reference to `cap_get_proc'
## Fix
add_link_options(-lcap)

# warning: ‘__builtin_strncpy’ output may be truncated
## Symptom
```
/usr/include/x86_64-linux-gnu/bits/string_fortified.h:106:10: warning: ‘__builtin_strncpy’ output may be truncated copying 16 bytes from a string of length 16 [-Wstringop-truncation]
```
## Fix
+ Add C Flag Option
```
-Wno-stringop-truncation -Wno-format-truncation
```
