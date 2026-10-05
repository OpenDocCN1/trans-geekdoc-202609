The terms WebAssembly and Wasm mean the same thing, and we'll use the term Wasm.

I've divided the chapter as follows:

+   * Pre-reqs
* Intro to Wasm
* Write a Wasm app
* Containerize a Wasm app
* Deploy a Wasm app

# Pre-reqs

You'll need all of the following if you plan on following along:

+   * Docker Desktop 4.30+ with Wasm enabled
* Rust 1.72+ with the Wasm target installed
* Spin 2.5+

At the time of writing, support for Wasm is a beta feature in Docker Desktop and doesn't work with Multipass Docker VMs. This may change in the future. It also means there's a higher risk of bugs. I've tested the examples in this chapter on Docker Desktop 4.30.0.

# Configure Docker Desktop for Wasm