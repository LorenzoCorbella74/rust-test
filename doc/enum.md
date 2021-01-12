[back](../README.md)

# Enum
Sono dei tipi che hanno un ristretto numero di valori (le varie opzioni sono dette "variants.")

```rust
enum Movement {
  // Variants
  Up,
  Down,
  Left,
  Right,
}

fn move_avatar(m: Movement) {
  // Perform action depending on info
  match m {
    Movement::Up => println!("Avatar moving up"),
    Movement::Down => println!("Avatar moving down"),
    Movement::Left => println!("Avatar moving left"),
    Movement::Right => println!("Avatar moving right"),
  }
}

pub fn run() {
  let avatar1 = Movement::Left;
  let avatar2 = Movement::Up;
  let avatar3 = Movement::Right;
  let avatar4 = Movement::Down;

  move_avatar(avatar1);
  move_avatar(avatar2);
  move_avatar(avatar3);
  move_avatar(avatar4);
}
```

Si hanno anche Enums con valori
```rust
enum Movement {
    Right(i32),
    Left(i32),
    Up(i32),
    Down(i32),
}

fn main() {
    let movement = Movement::Left(12);
}
```

E enum con varianti strutturate
```rust
enum Actions {
    StickAround,
    MoveTo { x: i32, y: i32},
}

fn main() {
    let action = Actions::MoveTo { x: 0, y: 0 };
}
```

Null non esiste mentre il tuple vuoto () rappresenta l'assenza di data (come l'undefined in javascript)

```rust
fn prints_but_returns_nothing(data: &str) -> () {
    println!("passed string: {}", data);
}
```


Il costrutto *match* permette di ...