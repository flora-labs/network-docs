# gentx submission

`gentx` submission process is crucial for validators who wish to participate in a new or upcoming Cosmos testnet. 
This document provides a step-by-step guide on how to generate and submit a `gentx` for validators who are looking to join the upcoming Cosmos testnet. 
The `gentx` (genesis transaction) is a special transaction used to register a validator in the genesis file of a new network.

## Prerequisites

Before proceeding, ensure you have:
- Successfully installed and set up your Cosmos node (`gaiad`). See the node installation guide [here](../../node-installation.md).


## Steps to Generate and Submit a Gentx

### 1. Initialize Your Validator Node

If not already initialized, set up your node with a unique moniker and chain ID:

```bash
gaiad init myvalidator --chain-id <testnet_chain_id>
```

### 2. Set Up Your Node

Create a new key or use an existing one for your validator:

```bash
gaiad keys add myvalidator
# or in case you want to use mnemonic you already have
gaiad keys add myvalidator --recover
```

Make a note of the address and mnemonic. **Keep your mnemonic safe**; it is your backup!


### 3. Add Genesis Account

Adjust the genesis configuration as necessary. For testnets, you might need to modify parameters like staking denominations:

```bash
gaiad add-genesis-account $(gaiad keys show myvalidator -a) 1000000uatom
```

### 4. Create the Gentx

Generate the `gentx` for your validator. Specify the amount to stake and the commission details:

```bash
gaiad gentx myvalidator 1000000uatom --chain-id <testnet_chain_id> \
  --commission-rate="0.10" --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" --min-self-delegation="1" \
  --pubkey $(gaiad tendermint show-validator)
```

This command creates a genesis transaction (`gentx`) for your validator with the specified staking, commission rates, and tendermint public key.

### 5. Submit Your Gentx

After generating your `gentx`, it will be located in `~/.gaia/config/gentx/`. For most testnets, you will need to submit this file to the designated repository or through a form provided by the testnet coordinators.

```bash
# Example submission command
cp ~/.gaia/config/gentx/gentx-<identifier>.json <path-to-testnet-gentx-submission>
```

Follow the specific instructions provided by the testnet organizers on how to submit the `gentx`.

## Post-Submission

- **Verification**: Ensure that your `gentx` has been accepted and included in the genesis file by checking the testnet's genesis transactions list or communicating with the testnet team.
- **Monitoring**: Once the testnet launches, monitor your validator node closely to ensure it is signing blocks and participating in consensus.

## Conclusion

Successfully generating and submitting your `gentx` is a key step in joining the Cosmos testnet as a validator. Ensure you follow each step carefully and maintain the security of your keys and node. Good luck!

This guide aims to ensure validators are well-prepared and understand the `gentx` submission process thoroughly, enhancing their participation in the testnet.
