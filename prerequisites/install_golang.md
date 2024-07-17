# Install Golang

The installation process varies based on the operating system. For development environments, installing Golang locally in the user's home directory allows developers to manage upgrades independently from the system's default packages and other users.

## Ubuntu 22.02 and later

### Download and Extract Golang

Instead of installing Golang system-wide, we recommend installing it in the user's home directory to allow developers to manage different Go versions based on project needs.


**For AMD and Intel compatible processors:**

```bash
GOVER=$(curl https://go.dev/VERSION?m=text | head -n 1)
wget https://golang.org/dl/${GOVER}.linux-amd64.tar.gz
mkdir -p ${HOME}/go/${GOVER}
tar -C ${HOME}/go/${GOVER} -xzf ${GOVER}.linux-amd64.tar.gz
```

**For ARM processors:**

```bash
GOVER=$(curl https://go.dev/VERSION?m=text | head -n 1)
wget https://golang.org/dl/${GOVER}.linux-arm64.tar.gz
mkdir -p ${HOME}/go/${GOVER}
tar -C ${HOME}/go/${GOVER} -xzf ${GOVER}.linux-arm64.tar.gz
```

**NOTE:** This approach ensures that the latest version of Go is installed locally for the user.

**Install a specific previous version (example uses go1.20.3):**
```bash
GOVER=go1.20.3
wget https://golang.org/dl/${GOVER}.linux-amd64.tar.gz
mkdir -p ${HOME}/go/${GOVER}
tar -C ${HOME}/go/${GOVER} -xzf ${GOVER}.linux-amd64.tar.gz
```

**Configure Environment Variables**

To ensure Go works correctly with your shell, append the following to your ${HOME}/.profile, ${HOME}/.bashrc, or appropriate configuration file:

```bash
# Set the Go environment variables dynamically based on installed version
GOVER=$(ls ${HOME}/go | tail -n 1)  # This assumes you have at least one version installed
GOROOT=${HOME}/go/${GOVER}
GOPATH=${HOME}/go
GOBIN=${GOPATH}/bin

export GOROOT GOPATH GOBIN
export PATH=${PATH}:${GOROOT}/bin:${GOBIN}
```

**NOTE:** To ensure the environment variables are set up correctly for new terminal sessions, users should log off and log on again after setup.


