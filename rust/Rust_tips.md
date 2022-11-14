# Rust tips
## Get argument variables
```
/* use */
use std::process;

/* in function */
let args: Vec<String> = env::args().collect();
```