## Pre-requisites


## Additional packages
```bash
apt install make clang pkg-config libssl-dev build-essential git jq llvm libudev-dev -y
```

## Create user account
```bash
adduser relayer
```

## Rust installation
As a `relayer` user
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```


# Relayer deployment

## Build Hermes
```bash
git clone https://github.com/informalsystems/ibc-rs.git && \
cd ibc-rs && \
git checkout v1.10.0 && \
cargo build --release --bin hermes
```

```bash
mkdir ~/.local/bin
cp ~/ibc-rs/target/release/hermes ~/.local/bin
```

## Create systemd service
```
[Unit]
Description=Hermes IBC Relayer

[Service]
User=relayer
Group=relayer
ExecStart=/home/relayer/.local/bin/hermes start
LimitNOFILE=180000
Restart=always
RestartSec=3
StandardOutput=append:/var/log/hermes.log
StandardError=append:/var/log/hermes.log

[Install]
WantedBy=multi-user.target
```


## Create configuration
That allows to automatically create configuration for selected chains
```bash
hermes config auto --output ./config.toml --chain CHAIN1 --chain CHAIN2
```

