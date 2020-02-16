# Snaps OpenRPC Generator

Generate High end snaps in a snap.

<center>
  <span>
    <img alt="CircleCI branch" src="https://img.shields.io/circleci/project/github/xops/snaps-openrpc-generator/master.svg">
    <img src="https://codecov.io/gh/xops/snaps-openrpc-generator/branch/master/graph/badge.svg" />
    <img alt="Dependabot status" src="https://api.dependabot.com/badges/status?host=github&repo=xops/snaps-openrpc-generator" />
    <img alt="Chat on Discord" src="https://img.shields.io/badge/chat-on%20discord-7289da.svg" />
    <img alt="npm" src="https://img.shields.io/npm/dt/@xops/snaps-openrpc-generator.svg" />
    <img alt="GitHub release" src="https://img.shields.io/github/release/xops/snaps-openrpc-generator.svg" />
    <img alt="GitHub commits since latest release" src="https://img.shields.io/github/commits-since/xops/snaps-openrpc-generator/latest.svg" />
    <img alt="js badge" src="https://img.shields.io/badge/js-javascript-yellow.svg" />
    <img alt="rs badge" src="https://img.shields.io/badge/rs-rust-brown.svg" />
  </span>
</center>


A Generator tool for creating [Metamask Snaps](https://github.com/MetaMask/snaps-cli) using [open-rpc](https://github.com/open-rpc/spec) APIs.

[Getting Started Video (Demo)](https://www.youtube.com/watch?v=46nJ4AWHmvw)


## Features:

- Can generate:
  - Clients for accessing your snap
  - Documentation
  - Snap Scaffold with strongly typed interfaces


## Install

```shell
$ npm install -g @xops.net/snaps-openrpc-generator
```

## Usage

### Using it in your project

Make a new folder for your Snap project
```shell
$ mkdir MySnap && cd MySnap
```

Write an OpenRPC Document that describes your plugins interface, and includes any documentation, examples, etc you may want. You can start with one of the [OpenRPC examples](http://github.com/open-rpc/examples), write your own with the help of the [OpenRPC Playground](playground.open-rpc.org), or start from the hello world snap:
```shell
echo '{
  "openrpc": "1.2.4",
  "info": {
    "title": "MySnap",
    "version": "1.0.0"
  },
  "methods": [
    {
      "name": "hello",
      "params": [],
      "result": {
        "name": "helloWorldResult",
        "schema": {
          "type": "string"
        }
      },
      "examples": [
        {
          "name": "helloWorldExample",
          "params": [],
          "result": {
            "name": "world",
            "value": "world"
          }
        }
      ]
    }
  ]
}' > openrpc.json
```

Create a generator config file

```shell
$ snaps-openrpc-generator init
```

Generate artifacts based on your config

```shell
$ snaps-openrpc-generator generate -c openrpc-generator-config.json
```

To build the snaps plugin:

```shell
cd snap
npm install .
npm run build
npm run serve
```

The resulting plugin is now at at `http://localhost:8081` and which hosts the `package.json` and `bundle.js` needed for snaps.

To build the documentation:

cd into `docs` directory, install and start
```shell
cd docs
npm install .
npm start
```

you can now open `http://localhost:8000` and view your generated, interactive documentation site.

<img width="1676" alt="snaps2" src="https://user-images.githubusercontent.com/364566/74609561-7cfe7480-50a8-11ea-950a-139cf26ad138.png">

and play around with the interactive api documentation at `http://localhost:8000`
<img width="1394" alt="demo_thing" src="https://user-images.githubusercontent.com/364566/74609566-87207300-50a8-11ea-8f41-eaf27625da16.png">



## Resources

- [@open-rpc/generator package](https://www.npmjs.com/package/@open-rpc/generator)
- [example open-rpc documents](https://github.com/open-rpc/examples/tree/master/service-descriptions)
