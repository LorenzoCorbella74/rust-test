[back](../README.md)

# Variabili

Rust è un linguaggio block-scoped dove cioè la visibilità delle variabili è contenuta dentro un blocco di codice identificato da *{ }*; alla fine del blocco la risorsa è rilasciata (drop).

 

Le variabili sono dichiarate usando la keyword  *let*. Quando si assegna un valore Rust è in grado di associare un tipo (o può essere aggiunto manualmente)

E' possibile assegnare un nome di variabile più volte: questo è detto *variable shadowing* e permette di cambiare il tipo della variabile più volte.

I nomi devono essere sempre in ___snake_case___ come da [convenzione](https://rust-lang.github.io/api-guidelines/naming.html).

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

