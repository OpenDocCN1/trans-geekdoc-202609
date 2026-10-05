Search the web for how to install Rust and follow the instructions for your platform.

Once you’ve installed Rust, run the following command to install the wasm32-wasmi target so that Rust can compile to Wasm.

```
$ rustup target add wasm32-wasmi
info: downloading component 'rust-std' for 'wasm32-wasmi'
info: installing component 'rust-std' for 'wasm32-wasmi'
```

# Install Spin

Spin is a Wasm framework and runtime that makes building and running Wasm apps easy.

Search the web for how to install Fermyon spin and follow the instructions for your system.

Run the following command to ensure it’s installed correctly.

```
$ spin --version
spin 2.5.0 (83eb68d 2024-05-08)
```

You’re now ready to build and run Wasm apps on your local machine.