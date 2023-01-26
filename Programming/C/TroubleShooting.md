# Symptom
+ unix-caps.c:(.text+0x1d): undefined reference to `cap_get_proc'
# Fix
add_link_options(-lcap)