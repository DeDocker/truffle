# truffle
Docker image of Truffle - simple development framework for Ethereum

# Supported tags and respective `Dockerfile` links

* `3.2`, `latest` [(Dockerfile)](https://github.com/DeDocker/truffle/blob/master/3.2/Dockerfile)
* `3.0` [(Dockerfile)](https://github.com/DeDocker/truffle/blob/master/3.0/Dockerfile)
* `2.1` [(Dockerfile)](https://github.com/DeDocker/truffle/blob/master/2.1/Dockerfile)

# Running tests with `testrpc`

Make sure that correct host is set in `truffle.js`.

It MAY look like this:

v2:

```js
module.exports = {
  rpc: {
    host: process.env.RPC_HOST || "localhost",
    port: 8545
  }
};
```

v3

```js
module.exports = {
  networks: {
    development: {
      host: process.env.RPC_HOST || "localhost",
      port: 8545,
      network_id: "*"
    }
  }
};
```

Run `testrpc` server instance:

```bash
docker run --rm -d --name testrpc -p 8545 desmart/testrpc:latest
```

And then run `truffle` tests:

```bash
docker run --rm -v "${PWD}:/usr/src/app" --link testrpc -e "RPC_HOST=testrpc" desmart/truffle:latest test
```
