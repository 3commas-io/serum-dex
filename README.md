<div align="center">
  <img height="170" src="http://github.com/project-serum/awesome-serum/blob/master/logo-serum.png?raw=true" />

  <h1>serum-rs</h1>

  <p>
    <strong>Project Serum Rust Monorepo</strong>
  </p>

  <p>
    <a href="https://travis-ci.com/project-serum/serum-dex"><img alt="Build Status" src="https://travis-ci.com/project-serum/serum-dex.svg?branch=master" /></a>
    <a href="https://discord.com/channels/739225212658122886"><img alt="Discord Chat" src="https://img.shields.io/discord/739225212658122886?color=blueviolet" /></a>
    <a href="https://opensource.org/licenses/Apache-2.0"><img alt="License" src="https://img.shields.io/github/license/project-serum/serum-dex?color=blue" /></a>
  </p>

  <h4>
    <a href="https://projectserum.com/">Website</a>
    <span> | </span>
    <a href="https://serum-academy.com/en/">Academy</a>
    <span> | </span>
    <a href="https://github.com/project-serum/awesome-serum">Awesome</a>
    <span> | </span>
    <a href="https://dex.projectserum.com/#/">DEX</a>
    <span> | </span>
    <a href="https://github.com/project-serum/serum-ts">TypeScript</a>
  </h4>
</div>

## Program Deployments on Solana

| Program | Devnet | Mainnet Beta |
| --------|--------|------------- |
| [DEX](/dex)     | `F9b23Ph1JdBev2fULXTZLzaxVh2nYVdMVq9CTEaEZrid` | `EUqojwWA2rd19FZrzeBncJsm38Jm1hEhE3zsmX3bRc2o` |
| [Registry](/registry/program) | `FigXetJcXogqm94qfmyKWy6U5KJAwtxSgJMjUHercVQp` | `Gw1XNGbSnx7PJcHTTuxxhWfkjjPmq29Qkv1hWbVFnrDp` |
| [Lockup](/lockup/program) | `CiNaYvdnQ42BNdbKvvAapHxiP18pvc3Vk5WuZ59ia64x` | `6GSn1woRF541HaiEWqNofYn8quzJuRBPi1nwoho8zNnh` |
| [Crank Rewards](/registry/rewards/program) | `nwEt8jsBDCjV5vNg9c5YN9ktyak314DCwVTTuA3Swd9` | `A6owGf3tHCcj7BfJe5MHQmoLNYjTZhrGYXo4HeAvJVbP `|

## Contributing

### Install Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustup component add rustfmt
```

On Linux systems you may need to install additional dependencies. On Ubuntu,

```bash
sudo apt-get install -y pkg-config build-essential python3-pip jq
```

### Install Solana

```bash
curl -sSf https://raw.githubusercontent.com/solana-labs/solana/v1.3.9/install/solana-install-init.sh | sh -s - v1.3.9
export PATH="/home/ubuntu/.local/share/solana/install/active_release/bin:$PATH"
```

### Download the source

```bash
git clone https://github.com/project-serum/serum-dex.git
```

### Install the BPF SDK

```bash
./do.sh update
```

## Running a local Solana cluster

The easiest way to run a local cluster is to run a docker container provided by Solana.
Instructions can be found [here](https://solana-labs.github.io/solana-web3.js/). For local development, however, it's often convenient to build and run a validator from [source](https://github.com/solana-labs/solana).

### Download the source

```bash
git clone https://github.com/solana-labs/solana --branch v1.4.14
cd solana
```

### Install dependencies

```bash
sudo apt-get install -y libssl-dev libudev-dev zlib1g-dev llvm clang
```

### Build the validator

```bash
cargo build --release
```

### Run the local cluster

```bash
export RUST_LOG=solana_runtime::system_instruction_processor=trace,solana_runtime::message_processor=info,solana_bpf_loader=debug,solana_rbpf=debug
NDEBUG=1 ./run.sh
```

### Configure the CLI

```bash
solana config set -u http://127.0.0.1:8899
```

### Create and fund your wallet

```bash
solana-keygen new
solana airdrop 100
```
