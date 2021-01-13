[back](../README.md)

# Ownership
In Rust la memoria viene gestita tramite un sistema di proprietà (ownership) che permette di non avere nè il Garbage collector nè l'allocazione ed il rilascio manuale della memoria. 

Tre sono le regole del'ownership:
- Una volta che assegno un valore ad una variabile, tale variabile "possiede" il valore fintanto che il blocco non finisce.  
- Ci può essere solo un "owner" alla volta
- quando l'owner va out of scope (il blocco che lo include termina) il valore viene rilasciato.

Poiché può esserci un solo proprietario alla volta, non posso provare ad assegnare il valore di una variabile a un altro utilizzando il nome della prima variabile se è stata allocata nell'heap. Se il tipo della variabile è primitivo (int, double, bool, ecc.), La riassegnazione copierà semplicemente il valore e NON cambierà la proprietà. 

Quando un proprietario è passato come argomento ad una funzione la proprietà è trasferita (moved), al parametro della funzione e dopo tale trasferimento la variabile della funzione originale non può essere usata. La proprietà può ache essere passata indietro come risultato di una funzione.

## Borrowing
 I riferimenti permettono, tramite l'operatore *&*, di prendere a prestito ___un valore senza prendere la proprietà___. Ci può essere ___un infinito numero di riferimenti non mutabili ad una variabile ad un certo momento, oppure, un unico riferimento mutabile___. Anche i riferimenti sono rilasciati come tutte le risorse e nessun riferimento può vivere più a lungo del suo proprietario (e questo previene il cattivo uso dei riferimenti che puntano a dati non esistenti (chiamati in C "dangling pointers")).

 Per prendere a prestito l'accesso con la possibilità di mutazione ad una risorsa si usa  l'operatore *&mut*. Un proprietario di una risorsa __non può essere spostato quando preso a prestito con possibilità di mutazione__.

```rust
pub fn run() {
  // Primitive Array
  let arr1 = [1, 2, 3];
  let arr2 = arr1;

  // With non-primitives, if you assign another variable to a piece of data, the first variable will no longer hold that value. You'll need to use a reference (&) to point to the resource

  // Vector
  let vec1 = vec![1, 2, 3];
  let vec2 = &vec1;

  println!("Values: {:?}", (&vec1, vec2));
}
```

```rust
struct Foo {
    x: i32,
}

fn do_something(f: Foo) {
    println!("{}", f.x);
    // f is dropped here
}

fn main() {
    let mut foo = Foo { x: 42 };
    let f = &mut foo;

    // FAILURE: do_something(foo) would fail because
    // foo cannot be moved while mutably borrowed

    // FAILURE: foo.x = 13; would fail here because
    // foo is not modifiable while mutably borrowed

    f.x = 13;
    // f is dropped here because it's no longer used after this point
    
    println!("{}", foo.x);
    
    // this works now because all mutable references were dropped
    foo.x = 7;
    
    // move foo's ownership to a function
    do_something(foo);
}

/* ------------------------------------------------------------------------- */

struct Foo {
    x: i32,
}

fn do_something(f: &mut Foo) {
    f.x += 1;
    // mutable reference f is dropped here
}

fn main() {
    let mut foo = Foo { x: 42 };
    do_something(&mut foo);
    // because all mutable references are dropped within
    // the function do_something, we can create another.
    do_something(&mut foo);
    // foo is dropped here
}
```

## Dereferencing
Usando riferimenti con &mut, è possibile settare il valore del proprietario tramite l'operatore *.

E' possibile fare una copia del valore posseduto usando l'operatore *  (se il valore può essere copiato).

```rust
fn main() {
    let mut foo = 42;
    let f = &mut foo;
    let bar = *f; // get a copy of the owner's value
    *f = 13;      // set the reference's owner's value
    println!("{}", bar);
    println!("{}", foo);
}
```

E' possibile avere riferimenti a riferimenti

```rust
struct Foo {
    x: i32,
}

fn do_something(a: &Foo) -> &i32 {
    return &a.x;
}

fn main() {
    let mut foo = Foo { x: 42 };
    let x = &mut foo.x;
    *x = 13;
    // x is dropped here allow us to create a non-mutable reference
    let y = do_something(&foo);
    println!("{}", y);
    // y is dropped here
    // foo is dropped here
}
```