[back](../README.md)

# Moduli
E' possibile frazionare il codice tramite l'utilizzo dei moduli. Ad esempio un file *prova.rs* può contenere varie elementi (funzioni, struct, ) che possono essere esposti all'esterno tramite la keyword *pub*. Di default i membri di un crate non sono accessibili dall'esterno!. Il modulo è poi importato secondo la seguente sintassi:

```rust
// nel file prova.rs
pub fn run() {
  greeting("Hello", "Jane");
}

// nel file main.rs si importa il contenuto del file prova.rs
mod prova;

fn main(){
    // si utilizza tramite la notazione >namespace>::<nome_fn>
    prova::run();
}
```

I moduli possono stare anche nello stesso file e vengono detti *inline module* ( e sono generalmente usati per attività di test).

``` rust
fn main() {
   greetings::hello();
}

// This macro removes this inline module when Rust 
// is not in test mode.
#[cfg(test)]
mod tests {
    // Notice that we don't immediately get access to the 
    // parent module. We must be explicit.
    use super::*;

    //... tests go here ...
}
```

In via generale ogni programma o libreria scritta in Rust è un *crate* ed ogni crate è fatto da una gerarchia di moduli: ogni crate ha un modulo root: se è un programma sta in *main.rs* se è una libreria in *lib.rs*

Ogni modulo può tenere variabili globali, funzioni, structs, traits e altri moduli, non c'è quindi una relazione 1 a 1 nella mappatura dell'albero dei moduli. Si deve costruire l'alberatura dei moduli manualmente nel codice.

Referencing Other Modules and Crates
Items nei modules possono essere referenziati tramite il loro percorso di modulo completo std::f64::consts::PI o, in una maniera più semplice tramite la keyword *use* che permette di specificare particolari item dai moduli senza mettere il path completo.

Un *crate* è una unità di compilatione in Rust. Quando rustc some_file.rs è chiamato, some_file.rs è trattato come un file crate. Se dentro some_file.rs ci stanno dichiarazioni di mod, allora il contenuto dei file dei moduli saranno inseriti al posto delle dichiarazioni dei moduli, prima di far girare il compilatore. In altre parole, i moduli non vengono compilati individualmente,ma soltanto i crates sono compilati.

Un crate può essere compilato in un file binario o in una libreria. Di default, rustc produrrà un binario da un crate a meno che non si passi il flag *--crate-type=lib* producendo un file *.rlib*.

```rust
use std::f64::consts::PI;

// Possono essere referenziati item Multiple in un singolo modulo con:
use std::f64::consts::{PI,TAU}

fn main() {
    println!("Welcome to the playground!");
    println!("I would love a slice of {}!", PI);
}
```

## Creare moduli e gerarchia
Rustpermette di creare moduli strettamente legati alla struttura dei file. E' possibile dichiarare un modulo *foo*:

+ creare un file foo.rs
+ creare una directory chiamata foo con dentro un file *mod.rs*

Un modulo può dipendere da un altro modulo. In modo da stabilire una relazione tra module e il suo sub-module, si deve scrivere nel parent module (cioè nel ricevente) *mod foo*: questa dichiarazione guarderà per un file chiamato 
foo.rs o foo/mod.rs e inserirà il suo contenuto  dentro un modulo chiamato foo sotto questo scope.

### Internal Module Referencing
Rust ha varie keywords nel path d'uso per accedere velocemente al modulo desiderato:

+ crate - il root module del tuo crate
+ super - il parent moduledel tuo modulo corrnte
+ self - il modulo corrnte