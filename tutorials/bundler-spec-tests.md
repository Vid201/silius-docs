# Bundler spec tests

There are two EIPs that describe the behavior of bundlers in ERC-4337:

* the main [ERC-4337: Account Abstraction Using Alt Mempool](https://github.com/eth-infinitism/account-abstraction/blob/develop/eip/EIPS/eip-4337.md)
* validation rules for bundlers: [Account Abstraction Validation Scope Rules](https://github.com/eth-infinitism/account-abstraction/blob/develop/eip/EIPS/eip-aa-rules.md)

To keep up with the latest updates from different bundler implementation teams, the [Eth Infinitism](https://github.com/eth-infinitism) (development team of the standard ERC-4337) created **bundler spec tests** - bundler compatibility tests. These tests are updated continuously, with more edge cases covered and possibly new rules introduced to the standard.

You can find spec tests in the following repos:

* [bundler-spec-tests](https://github.com/eth-infinitism/bundler-spec-tests): bundler specification test suites
* [bundler-spec](https://github.com/eth-infinitism/bundler-spec): JSON schema RPC specs
* [bundler-test-executor](https://github.com/eth-infinitism/bundler-test-executor): execute spec-test against different bundler implementations

### Running bundler spec tests

First, you need to clone the bundler spec tests repo:

```
git clone https://github.com/eth-infinitism/bundler-spec-tests.git
```

Move to the cloned directory and initialize the repo (check requirements in the repo's README):

```
cd bundler-spec-tests
pdm install && pdm run update-deps
```

Before you can start the tests, you need to have geth node and Silius running. In the root folder of the Silius, start geth node and bundler:

```
// start geth
cd bundler-spec-tests
docker compose up -d
cd ..

// start bundler - you need to enable debug RPC interface for spec tests
make run-silius-debug // cargo run --release -- bundler --eth-client-address ws://127.0.0.1:8546 --mnemonic-file ${HOME}/.silius/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --beneficiary 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --entry-points 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789 --http --ws --http.api eth,debug,web3 --ws.api eth,debug,web3
```

After the geth and bundler are running, you can start the tests in the bundler-spec-tests folder:

```
pdm run pytest -rA -W ignore::DeprecationWarning --url http://127.0.0.1:3000 --entry-point 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789 --ethereum-node http://127.0.0.1:8545
```

That's it! All tests should pass. If any of the tests fail, please open a new [issue](https://github.com/silius-rs/silius/issues).

### Results

You can find the latest results [**here**](https://bundler-test-results.erc4337.io/) or on the [**ERC-4337 website**](https://www.erc4337.io/bundlers).

\
