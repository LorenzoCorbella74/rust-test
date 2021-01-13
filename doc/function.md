[back](../README.md)

# Funzioni

In rust le funzioni identificate dalla keyword *fn* permettono di riutilizzare dei blocchi di codice. I nomi delle funzioni devono essere in snake_case.

```rust
fn greeting(greet: &str, name: &str) {
  println!("{} {}, nice to meet you!", greet, name);
}

// come in JS si possono legare a variabili dei function values
let get_sum = add(5, 5);
println!("Sum: {}", get_sum);

// possono ritornare più valori 
fn swap(x: i32, y: i32) -> (i32, i32) {
    return (y, x);
}

fn main() {
    // return a tuple of return values
    let result = swap(123, 321);
    println!("{} {}", result.0, result.1);

    // destructure the tuple into two variables names
    let (a, b) = swap(result.0, result.1);
    println!("{} {}", a, b);
}
```
E' possibile specificare i valori di ritorno con il simbolo *->* e se si restituisce un valore nell'ultima riga della funzione, non è necessario includere la keyword *return*-


## Closure
Si indica per closure ciò che in javascript sono le arrow function. Al posto di *()=> ()* si ha *| | ()*.

```rust
// al posto di
fn add(n1: i32, n2: i32) -> i32 {
  n1 + n2
}

// si può usare una Closure
let n3: i32 = 10;

let add_nums = |n1: i32, n2: i32| n1 + n2 + n3;

println!("C Sum: {}", add_nums(3, 3));
```

