# rust-wasm-note

Use rust-up to install Rust and wasm-pack on macOS

PS. do Not install Rust using Homebrew, it will cause some issues when using wasm-pack.

```bash
brew uninstall rust && brew install rustup-init && rustup-init
brew install wasm-pack
```

## Write WASM Module using Rust

https://developer.mozilla.org/en-US/docs/WebAssembly/Rust_to_Wasm


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

loading up the wasm module and calling it from javascript

```html
    <script type="module">
      import init, { add } from './pkg/hello_wasm.js'
      await init()
      console.log(add(1, 2))
    </script>
```
