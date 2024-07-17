# Install Cosmovisor

Cosmovisor is a process manager for Cosmos SDK applications that simplifies the upgrade process. It monitors the blockchain's governance proposal system for pending upgrades, automatically downloads binaries, and can perform automatic restarts.

## Build Cosmovisor

1. **Clone the repository and navigate to the Cosmovisor directory**:
   ```bash
   cd ${HOME}
   git clone https://github.com/cosmos/cosmos-sdk && cd cosmos-sdk/tools/cosmovisor/
   ```

   This step involves retrieving the latest version of Cosmovisor from the official Cosmos SDK repository.

2. **Build the application**:
   ```bash
   make
   ```

   The `make` command compiles the Cosmovisor source code, producing an executable binary.

3. **Install the binary globally**:
   ```bash
   sudo cp cosmovisor /usr/local/bin
   ```

   Copying the Cosmovisor binary to `/usr/local/bin` makes it accessible system-wide, allowing any user to run it.


## Service File Template

A service file template helps in automating the node's operations using `systemd`, a system and service manager in Unix-like operating systems.

```bash
[Unit]
Description=Chain Node Name
After=network-online.target

[Service]
User=<USER>
Group=<GROUP>
ExecStart=/usr/local/bin/cosmovisor run start
Restart=always
RestartSec=3
LimitNOFILE=4096
Environment="DAEMON_NAME=<NODE_BINARY_NAME>"
Environment="DAEMON_HOME=<NODE_HOME_FOLDER>"
Environment="DAEMON_ALLOW_DOWNLOAD_BINARIES=false"
Environment="DAEMON_RESTART_AFTER_UPGRADE=true"
Environment="DAEMON_LOG_BUFFER_SIZE=512"
Environment="UNSAFE_SKIP_BACKUP=true"

[Install]
WantedBy=multi-user.target
```

- **Description and Dependency**: Describes the service and specifies that it should start after the network is available.
- **Service Settings**: Defines user, group, startup command, restart conditions, and environmental variables that configure how Cosmovisor runs the node.
- **Installation**: Specifies the target type, ensuring the service is integrated into the system's multi-user environment.

## Managing the Service

These commands control and monitor the node service:

- **Reload systemd**: Updates systemd to recognize changes to service files.
  ```bash
  systemctl daemon-reload
  ```
- **Start the service**: Activates the node service.
  ```bash
  systemctl start <service>
  ```
- **Monitor logs**: Tracks the running service's output in real time.
  ```bash
  journalctl -u <service> -f
  ```
