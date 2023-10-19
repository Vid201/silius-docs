# Project structure

The project is a standard Rust workspace with multiple crates - each responsible for specific functionalities. Each crate can also be imported into any other project, bootstrapping building account abstraction projects in Rust.

At the moment, the following crates are available:

* [**primitives**](../crates/primitives.md) - types, constants, and other basic primitives&#x20;
* [**contracts**](../crates/contracts.md) - interface for entry point smart contract and debug tracing utilities
* [**uopool**](../crates/uopool.md) - implementation of user operation mempool, validation logic (canonical and alt mempools), reputation
* [**bundler**](../crates/bundler.md) - implementation of the bundling functionalities (bundle builder)
* [**rpc**](../crates/rpc.md) - implementation of JSON-RPC interfaces, HTTP and WS
* [**grpc**](../crates/grpc.md) - crate that implements logic for running components (uopool and bundler) as gRPC services

<figure><img src="../.gitbook/assets/project_structure.png" alt="" width="375"><figcaption></figcaption></figure>
