# Screen
+ Exit Screen
^A ^D

+ Add Screen
screen -AmdS {screen_name} bash&

+ Send command to screen
screen -S {screen_name} -X stuff $'{command}\r'&

+ Kill process
pkill -9 {process_name}

+ Scrollback option
```
ctrl + A 
:
scrollback 30000
```