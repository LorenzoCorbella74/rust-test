# Installation

[back](../README.md)

Andare al [sito ufficiale](https://www.rust-lang.org/it/tools/install) e per Windows10 scaricare l'eseguibile e i [C++ Build tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/).

Il pacchetto installa:
+ *rustup*: CLI per gestire le versioni di rust e tool associati
+ *rustc*: il compilatore
+ *cargo*: il  build system ufficiale e dependancy manager

```bash
# per installare l'ultima versione
$ rustup udate

# per disinstallare
$ rustup self uninstall

# L'installazione prevede una copia locale della documentazione
$ rustup doc

# Per vedere la versione del compilatore
$ rustc --version

# aggiungere tool
$ rustup component add rustfmt
$ rustup component add clippy
$ cargo tree
```

Una volta creato un file con estenzione *.rs* è possibile compilare il file tramite *rustc nome_file.rs* che genera un file binario eseguibile che è possibile far girare tramite *./nome_file.exe* oppure utilizzare cargo con i seguenti comandi:

```bash
# help
$ cargo --help

# Per vedere la versione 
$ cargo --version

# per creare un nuovo progetto (con git)
$ cargo new nome_progetto
# per creare un nuovo progetto in directory esistente
$ cargo init

# per compilare e produrre un eseguibile di 
# progetto dentro la directory target/debug
$ cargo build 

# per compilare ed esguire il progetto
$ cargo run 

# E' possibile "controllare" il codice per vedere se compila
# senza produrre un eseguibile (è + veloce di cargo build)
$ cargo check

# Per compilare una release ottimizzata
$ cargo build --release

# Per eseguire i test
$ cargo test


```

Tramite cargo si gestiscono le dipendenze del progetto chiamate *crates* riportate nel file *Cargo.toml* (analogo del package.json per i progetti  node.js), che vengono scaricati dal registry della community di rust [Crates.io](https://crates.io) e compilati insieme al codice del progetto.
```toml
[package]
name = "hello_cargo"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"
[dependencies]
rand = "0.3.14" # scarica l'ultima versione compatibile con la 0.3.14
```

Quando Cargo builda per la prima volta un progetto produce un file *Cargo.lock* su cui vengono scritte le versioni delle dipendenze. Se queste in futuro vengono aggiornate si dovrà fare manualmente un *cargo update* o scrivere sul cargo.toml la versione major richiesta.

## Links
+ [Rustc book](https://doc.rust-lang.org/rustc/index.html)
+ [Cargo book](https://doc.rust-lang.org/cargo/index.html)
+ [Lista crates](https://lib.rs/)


