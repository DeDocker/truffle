# truffle
Docker image of Truffle - simple development framework for Ethereum

# Supported tags and respective `Dockerfile` links

* `2.1`, `latest` [(Dockerfile)](https://github.com/DeDocker/truffle/blob/master/2.1/Dockerfile)

# Running tests with `testrpc`

Make sure that correct host is set in `truffle.js`.

It MAY look like this:

```js
module.exports = {
  rpc: {
    host: process.env.RPC_HOST || "localhost",
    port: 8545
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
