# Running in Docker

You can also run Silius in **Docker**. :whale:

The image is available on [**GitHub Container Registry**](https://github.com/silius-rs/silius/pkgs/container/silius).

```
docker run --net=host -v ./bundler-spec-tests/keys/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266:/data/silius/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 -v ./db:/data/silius/db ghcr.io/silius-rs/silius:latest bundler --eth-client-address http://127.0.0.1:8545 --datadir data/silius --mnemonic-file data/silius/0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --beneficiary 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 --entry-points 0x5ff137d4b0fdcd49dca30c7cf57e578a026d2789 --http --http.addr 0.0.0.0 --http.port 3000 --http.api eth,debug,web3 --ws --ws.addr 0.0.0.0 --ws.port 3001 --ws.api eth,debug,web3 --eth-client-proxy-address http://127.0.0.1:8545
```

You can also find [`docker-compose.yml`](https://github.com/silius-rs/silius/blob/main/docker-compose.yml) and [`Dockerfile`](https://github.com/silius-rs/silius/blob/main/Dockerfile) for building image in the [repo](https://github.com/silius-rs/silius/).

<figure><img src="../.gitbook/assets/containers_docker.png" alt="" width="375"><figcaption></figcaption></figure>
