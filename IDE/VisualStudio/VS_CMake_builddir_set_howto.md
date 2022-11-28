
1. Click below
+ CMake(K) -->  CMake 설정 변경(S) --> {Project Name}
2. Change below
```

### Old ###
"buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",

### New ###
"buildRoot": "${projectDir}\\out\\build\\${name}",

```