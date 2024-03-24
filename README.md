# rust-wasm-note

Use rust-up to install Rust and wasm-pack on macOS

PS. do Not install Rust using Homebrew, it will cause some issues when using wasm-pack.

```bash
brew uninstall rust && brew install rustup-init && rustup-init
brew install wasm-pack
```

## Write WASM Module using Rust

```bash
cargo new --lib hello-wasm
cd hello-wasm
```

Edit `Cargo.toml`:

```toml
# ensure the correct flags get passed to the rust compiler
[lib]
crate-type = ["cdylib"] # d dynamic library

[dependencies]
wasm-bindgen = "0.2.92"
```


build

```bash
wasm-pack build --target web
```



