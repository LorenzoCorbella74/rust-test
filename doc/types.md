[back](../README.md)

# Tipi

Rust è un linguaggio "statically typed" cioè deve conoscere il tipo di ogni variabile durante la fase di compilazione anche se il compilatore può assegnare (infer) il tipo basandosi sul valore indicato.

I tipi primitivi sono:
- Integers: u8, i8, u16, i16, u32, i32, u64, i64, u128, i128 (number of - bits they take in memory)
- Floats: f32, f64
- Boolean (bool)
- Characters (char) singolo carattere
- Tuples
- Arrays
- str


```rust
pub fn run() {
  // Default is "i32"
  let x = 1;

  // Default is "f64"
  let y = 2.5;

  // Add explicit type
  let z: i64 = 4545445454545;

  let t = 'x';
  let y: char = '😎';

  // Find max size
  println!("Max i32: {}", std::i32::MAX);
  println!("Max i64: {}", std::i64::MAX);

  // Boolean
  let is_active: bool = true;

  // Get boolean from expression
  let is_greater: bool = 10 < 5;

  let a1 = 'a';
  let face = '\u{1F600}';

  println!("{:?}", (x, y, z, is_active, is_greater, a1, face));
}
```


I tipi composti sono:
- struct
- tuples
- tuple structs
- enums

```rust
// struct
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let p = Point { x: 1, y: 1 };
    // field access
    println!("{}", p.x);
    println!("{}", p.y);
}

// tuple
fn main() {
    let t = (1, 2);
    println!("{}", t.0);
    println!("{}", t.1);
}

// tuple struct
struct Point(i32,i32);

fn main() {
    let ts = Point(1, 2);
    println!("{}", ts.0);
    println!("{}", ts.1);
}
```