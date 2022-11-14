# Rust tips
## Get argument variables
```
/* use */
use std::process;

/* in function */
let args: Vec<String> = env::args().collect();
```

## Handle Result<T>
```
let socket = match UdpSocket::bind("127.0.0.1:44221") {
    Ok(socket) => socket,
    Err(error) => {
        println!("Can't bind socket: {:?}", error)
        process::exit(1);
    }
};
```
### Other ways to handle
 + with unwrap()
```
/* This may cause panic! */
let socket = match UdpSocket::bind("127.0.0.1:44221").unwrap();
```
 + with expect()
```
/* This may cause panic! with custom error message*/
let socket = match UdpSocket::bind("127.0.0.1:44221")
    .expect("Can't bind socket");
```

## Cargo command cheatsheet
## Create new executable
### With new folder
 - cargo new {pkgname}
### Without new folder
 - cargo init .

## Build
### Debug
 - cargo build
### Release
 - cargo build --release

 ## Run
  - cargo run {-- args} 