# Running separate components

Since the architecture of the Silius bundler is [modular](../overview/architecture.md), you can run all components together or only a single component (based on your use case needs).

There are 4 commands available within Silius binary:

* bundler - runs all components
* bundling - runs the bundling component
* uopool - runs the user operation mempool
* rpc - runs the RPC API

Bundler:

```
cargo run --release -- bundler --eth-client-address http://127.0.0.1:8545 --mnemonic-file ${HOME}/.silius/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --beneficiary 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --entry-points 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789 --http --ws
```

Bundling component:

```
cargo run --release -- bundling --eth-client-address ws://127.0.0.1:8546 --mnemonic-file ${HOME}/.silius/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --beneficiary 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --entry-points 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789
```

User operation mempool:

```
cargo run --release -- uopool --eth-client-address ws://127.0.0.1:8546 --entry-points 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789
```

RPC:

```
cargo run --release -- rpc --http --ws
```

You can also run all commands in [Docker](docker.md).
