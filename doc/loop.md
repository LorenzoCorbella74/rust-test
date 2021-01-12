[back](../README.md)

# Loops
Come per tutti i linguaggi di programmazione sono utilizzati per iterare finchè una condizione è soddisfatta. Rust prevede tre costrutti:
+ loop
+ while loop
+ for in 

```rust
// Loop permette di ritornare valori (can break to return value)
fn main() {
    let mut x = 0;
    let v = loop {
        x += 1;
        if x == 13 {
            break "found the 13";
        }
    };
    println!("from loop: {}", v);
}


let mut count = 0;

// While Loop (FizzBuzz)
while count <= 100 {
    if count % 15 == 0 {
        println!("fizzbuzz");
    } else if count % 3 == 0 {
        println!("fizz");
    } else if count % 5 == 0 {
        println!("buzz")
    } else {
        println!("{}", count);
    }
    // Inc
    count += 1;
}

// For Range
for x in 0..100 {
    if x % 15 == 0 {
      println!("fizzbuzz");
    } else if x % 3 == 0 {
      println!("fizz");
    } else if x % 5 == 0 {
      println!("buzz")
    } else {
      println!("{}", x);
    }
  }
}
```