# System Configuration

## Prerequisites
[01. Golang install](install_golang.md)  
[02. Cosmovisor install](install_cosmovisor.md)

## Ubuntu
```
# Base
sudo apt-get install make gcc

# Golang
wget https://go.dev/dl/go1.22.1.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go1.22.1.linux-amd64.tar.gz
echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.bashrc
export PATH=$PATH:/usr/local/go/bin

```
 
## MacOS
```
# Base
brew install make
brew install gcc

# Golang
brew install go
```
