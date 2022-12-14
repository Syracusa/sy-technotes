# Rust tips


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



## Code snippet
### Handle String in Rust
+ https://doc.rust-lang.org/book/ch08-02-strings.html
```
// Create new string
let mut s = new String::new();

// From literal
let s = “Initial”.to_string();
let s = String::from(“Initial”);

// Append
let mut s = “foo”.to_string();
s.push_str(“bar”);
s.push(‘a’); // Single character

// Concatenation
let s1 = “Hello “.to_string();
let s2 = “world”.to_string();
let s3 = format!(“{}{}”, s1, s2); // s1 is still valid
let s4 = s1 + &s2; // s1 is now invalid
```

+ You cant get character from string with index. Use slice with care(May panic because it is UTF-8 encoded string)
```
// Per bytes
for b in “안녕”.bytes() {
  println!(“{}”, b);
}
// Per UTF-8 Characters
for c in “안녕”.chars() {
  println!(“{}”, c);
}
```

### Use HashMap
+ https://doc.rust-lang.org/book/ch08-03-hash-maps.html
```
// Use HashMap
 use std::collections::HashMap;

// Create empty hashmap and inserts element
let mut h = HashMap::new();
h.insert(“red”.as_string(), 0xFF0000);
```
+ Hashmap should have all same types in their elements. Per <k, v>, all k should be same type and same on v.
```
// Get value from hashmap
h.get(“red”.as_string()).copied().unwrap_or(0);

// iterate hashmap
for (k, v) in &h {
  println!(“{} {}”, k, v);
}

// Overwriting value
h.insert(“red”.as_string(), 0xFF0000);
h.insert(“red”.as_string(), 0xEE0000);

// Insert if not exist
let blue = h.entry(“Blue”. as_string()).or_insert(0x0000FF);
```