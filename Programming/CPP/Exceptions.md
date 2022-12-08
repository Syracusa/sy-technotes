# CPP Exception howto
---
## Basic example
```
#include <stdexcept>
#include <iostream>

void do_throw()
{
    throw std::runtime_error("Test error");
}

int main()
{
    try {
        do_throw();
    } catch(std::exception& e) {
        std::cout << "Exception caught\n" << e.what();
    }
}
```

## Standard exception
```
std::exception
L std::runtime_error
  L std::range_error
  L std::overflow_error
  L std::underflow_error
L std::logic_error
  L std::domain_error  
  L std::length_error
  L std::out_of_range
  L std::invalid_argument
```


