# MATRIX Chain User Guide (TESTNET)
---

### About
The MATRIX repository is based on go-ethereum which contains protocol changes to support the MATRIX protocol and a few other distinct features. This implements the MATRIX cryptocurrency, which maintains a separate ledger from the ETHEREUM network, for several reasons, the most immediate of which is that the consensus protocol is different.

### Getting Started
Welcome! This guide is intended to get you running on the MATRIX testnet. To ensure your client behaves gracefully throughout the setup process, please check your system meets the following requirements:


| OS      | Windows, Mac                                 |
|---------|----------------------------------------------|
| CPU     | 6 Core (Intel(R) Xeon(R) CPU X5670 @2.93GHz) |
| RAM     | 8G                                           |
| Free HD | 500G                                         |



### Build from Source

First of all, you need to clone the source code from MATRIX repository:

Git clone https://github.com/MatrixAINetwork/MATRIXAIPOC_GO.git, or

wget https://github.com/MatrixAINetwork/MATRIXAIPOC_GO/archive/master.zip

Building geth requires both a Go (version 1.7 or later) and a C compiler. You can install them using your favourite package manager. Once the dependencies are installed, run:

    cd MATRIXAIPOC_GO
    make geth
or, to build the full suite of utilities:

    make all


### Configuration
As an alternative to passing the numerous flags to the geth binary, you can also pass a configuration file via:

    $ geth --config /path/to/your_config.toml

To get an idea how the file should look like you can use the dumpconfig subcommand to export your existing configuration:

    $ geth --your-favourite-flags dumpconfig

Note: This works only with geth v1.6.0 and above.


### Full node on the MATRIX test network

Transitioning towards developers, if you'd like to play around with creating MATRIX contracts, you
almost certainly would like to do that without any real money involved until you get the hang of the
entire system. In other words, instead of attaching to the main network, you want to join the **test**
network with your node, which is fully equivalent to the main network, but with play money only.

    $ geth --testnet --fast --cache=512 console


### Docker Quick Start

One of the quickest ways to get MATRIX up and running on your machine is by using Docker:

docker build –t image_name

    docker run -d  -p 8545:8545 –p 30303:30303 –p 40404:40404 imagename --fast --cache=512

This will start geth in fast-sync mode with a DB memory allowance of 1GB just as the above command does.  It will also create a persistent volume in your home directory for saving your blockchain as well as map the default ports. There is also an `alpine` tag available for a slim version of the image.

Do not forget `--rpcaddr 0.0.0.0`, if you want to access RPC from other containers and/or hosts. By default, `geth` binds to the local interface and RPC endpoints is not accessible from the outside.