# Bit operation
+ Reference : https://stackoverflow.com/questions/47981/how-do-i-set-clear-and-toggle-a-single-bit
## Setting a bit
number |= 1UL << n;
## Clearing a bit
number &= ~(1UL << n);
## Toggling a bit
number ^= 1UL << n;