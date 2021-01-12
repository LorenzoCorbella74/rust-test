[back](../README.md)

## Variabili

Rust è un linguaggio block-scoped dove cioè la visibilità delle variabili è contenuta dentro un blocco di codice identificato da *{ }*.

 

Le variabili sono dichiarate usando la keyword  *let*. Quando si assegna un valore Rust è in grado di associare un tipo (o può essere aggiunto manualmente)

E' possibile assegnare un nome di variabile più volte: questo è detto *variable shadowing* e permette di cambiare il tipo della variabile più volte.

I nomi devono essere sempre in ___snake_case___.

Le variabili possono tenere sia "primitive data" che "references to data".

Le variabili possono essere:
- immutabili: In Rust le variabili sono *immutable by default* 
- mutabili: Per avere delle variabili il cui valore può cambiare si deve specificare usando la keyword *mut*.

### Constants
A differenza delle variabili, le costanti devono sempre avere tipi espliciti. I nomi delle costanti sono sempre presenti in SCREAMING_SNAKE_CASE.




```rust
pub fn run() {

    // si usa la keyword let
    let name = "Brad";

    // una variabili MUTABILE deve specificare la keyword "mut"
    let mut age = 37;
    println!("My name is {} and I am {}", name, age);
    age = 38;
    println!("My name is {} and I am {}", name, age);

    // per le constanti si usa la keyword "const"
    // e deve sempre essere tipizzata
    const ID: i32 = 001;
    println!("ID: {}", ID);

    // Assign multiple vars
    let ( my_name, my_age ) = ("Brad", 37);
    println!("{} is {}", my_name, my_age );
}
```

# Ownership  & Borrowing
Poiché Rust non effettua il garbage-collect e i programmatori non devono allocare e rilasciare manualmente la memoria, la memoria viene gestita tramite un sistema di proprietà (ownership). Tre sono le regole del'ownership:
- Una volta che assegno un valore ad una variabile, tale variabile "possiede" il valore fintanto che il blocco non finisce.  
- Ci può essere solo un "owner" alla volta
- quando l'owner va out of scope (il blocco che lo include termina) il valore viene rilasciato.

Poiché può esserci un solo proprietario alla volta, non posso provare ad assegnare il valore di una variabile a un altro utilizzando il nome della prima variabile se è stata allocata nell'heap. Se il tipo della variabile è primitivo (int, double, bool, ecc.), La riassegnazione copierà semplicemente il valore e NON cambierà la proprietà. 


## Borrowing
Per puntare ad una risorsa si usa dei "Reference Pointers" cioè dei riferimenti a specifiche risorse in memoria. I riferimenti permettono di prendere ___il valore senza prendere la proprietà___. Ci può essere ___un infinito numero di riferimenti non mutabili ad una variabile ad un certo momento, oppure, un unico riferimento mutabile___.

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
