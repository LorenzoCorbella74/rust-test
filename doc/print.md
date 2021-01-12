[back](../README.md)

## Main Fn
La funzione main funge da inizializzatore del codice rust. 

```rust
fn main () {
    println!("Hello world");
}
```
## Comments
Sono supportati anche i commenti innestati ma per convenzione sono da evitare.
```rust
// Line comments
/* Block comments */
```

## Print fn

La funzione *print* e *println* sono due macro del linguaggio pertanto presentano la *!* prima delle *()*. La seconda permette di avere un *\n* in fondo alla stringa che viene scritta in console

```rust
pub fn run() {

  // sono identiche
  print!("Hello from the print.rs file\n");
  println!("Hello from the print.rs file");

  // Basic Formatting
  println!("{} is from {}", "Brad", "Mass");

  // Positional Arguments
  println!(
    "{0} is from {1} and {0} likes to {2}",
    "Brad", "Mass", "code"
  );

  // Named Arguments
  println!(
    "{name} likes to play {activity}",
    name = "John",
    activity = "Baseball"
  );

  // Placeholder traits
  println!("Binary: {:b} Hex: {:x} Octal: {:o}", 10, 10, 10);

  // Placeholder for debug trait
  println!("{:?}", (12, true, "hello"));

  // Basic math
  println!("10 + 10 = {}", 10 + 10);
}
```