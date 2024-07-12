# Node Installation Documentation for Cosmos (Gaia)

## Prerequisites

Before proceeding with the installation of the Cosmos node, ensure that the following prerequisites are met:

- **Operating System**: Ubuntu 22.04 LTS or newer.
- **Golang**: Version 1.22.x or newer. Refer to the detailed installation guide [here](../../home/installation-guides/install-golang.md).
- **JSON Processor (jq)**: Required for parsing JSON outputs.
  ```bash
  sudo apt install jq
  ```
- **Essential Build Tools**: Necessary for building from source.
  ```bash
  sudo apt install build-essential
  ```

#### Installation Steps

##### 1. Create a Non-Root User (if not already existing)

For security reasons, it is recommended to run blockchain nodes as a non-root user:

```bash
sudo adduser gaiauser
sudo usermod -aG sudo gaiauser  # Only if admin privileges are needed
su - gaiauser
```

##### 2. Clone the Repository

As the gaiauser, clone the Gaia repository into your home directory:

```bash
cd ~
git clone https://github.com/cosmos/gaia.git
cd gaia
```

##### 3. Build from Source

Compile the source code to build the Gaia daemon (gaiad):

```bash
make install
```

This command will build the `gaiad` binary and install it in `~/go/bin`.

##### 4. Initialize the Node

Set up your node:

```bash
gaiad init <MYNODE> --chain-id cosmoshub-4
```

Replace `<MYNODE>` with your desired node name. This step configures your node and creates necessary configuration files in `~/.gaia`.

##### 5. Configure the Node

Edit the configuration files to tune parameters such as the minimum gas prices and other network settings:

```bash
nano ~/.gaia/config/config.toml
nano ~/.gaia/config/app.toml
```

##### 6. Add Genesis File

Download and place the genesis file into the correct directory:

```bash
wget -O ~/.gaia/config/genesis.json https://raw.githubusercontent.com/cosmos/mainnet/master/genesis.json
```

##### 7. Start the Node

Begin syncing the blockchain:

```bash
gaiad start
```

This command starts the node, which will begin to sync with the Cosmos network. You can monitor the logs to check the progress.

### Post-Installation Steps

- **Security Enhancements**: Configure firewalls and secure the node by limiting access to node-specific ports.
- **Monitoring**: Set up monitoring tools like Prometheus and Grafana to keep track of the node's performance and health.
- **Regular Updates**: Stay updated with the latest software releases and security patches.

### Conclusion

This setup ensures that the node operates in a user-specific environment, enhancing the security and manageability of the node. It is scalable to more complex setups such as sentry node architectures or validator nodes in staking scenarios.

### Note for macOS Users

A similar approach can be adopted for macOS, using Homebrew for dependencies and adjusting paths and environment settings accordingly. The specifics for macOS can be developed following the structure laid out for Ubuntu.

This documentation aims to be comprehensive, guiding a user through each step while providing the rationale and necessary background information to manage a Cosmos node effectively.
