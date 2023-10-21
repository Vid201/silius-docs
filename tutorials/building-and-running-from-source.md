# Building and running from source

Silius is built in Rust. [First install Rust](https://www.rust-lang.org/tools/install), then clone the repository and enter the directory.

```
git clone git@github.com:Vid201/silius.git
cd silius
```

At the moment, the recommended version of Rust is 1.71.1.

### Build from source

Before you can build the project, you need some prerequisites installed:

1. `libclang-dev`, `pkg-config` and `libssl-dev` on Debian/Ubuntu.
2. Ethereum execution client JSON-RPC API with enabled [`debug_traceCall`](https://geth.ethereum.org/docs/interacting-with-geth/rpc/ns-debug#debug\_tracecall). For production, you can use [Geth](https://github.com/ethereum/go-ethereum) or [Erigon](https://github.com/ledgerwatch/erigon). For testing, we are using Geth dev mode (tested with [v1.12.0](https://github.com/ethereum/go-ethereum/releases/tag/v1.12.0)); so you need to install [Geth](https://geth.ethereum.org/docs/getting-started/installing-geth) for running tests.
3. [`solc`](https://docs.soliditylang.org/en/v0.8.17/installing-solidity.html) >=0.8.12.
4. [`cargo-sort`](https://crates.io/crates/cargo-sort) and [`cargo-udeps`](https://crates.io/crates/cargo-udeps).

There are also some other third-party dependencies you need to setup (mainly ERC-4337 related smart contracts). These commands will clone the account abstraction repos and compile the smart contracts.

```
make fetch-thirdparty
make setup-thirdparty
```

After everything is setup, you can start the build:

```
make build // cargo build --release
```

### Running

You can now run the Silius with the following command:

```
make run-silius // cargo run --release -- bundler --eth-client-address http://127.0.0.1:8545 --mnemonic-file ${HOME}/.silius/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --beneficiary 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --entry-points 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789 --http --ws
```

Some of the most commonly used CLI params are:

* `eth-client-address`: HTTP or WS address to the Ethereum execution client (client should have `debug` RPC interface enabled, if not you need to run the bundler in unsafe mode with `--uopool-mode unsafe`)
* `mnemonic-file`: path to the seed phrase of the bundler's account
* `datadir`: path to the folder where db file will be saved (in case the storage is database)
* `beneficiary`: address to where the gas left is sent
* `entry-points`: address of the ERC-4337 singleton entry point smart contract
* `http`: enable HTTP JSON-RPC endpoints
* `ws`: enablr WS JSON-RPC endpoints
* `eth-client-proxy-address`: HTTP address to the Ethereum execution client, where to forward the standard calls to the execution client
