# Managing Keys

## Create a New Key
```bash
florad keys add <KEY_NAME>
```
- `<KEY_NAME>`: Replace this with your desired key name.
- This command generates a new key with the specified name and prints the address, public key, and mnemonic.

## Import a Key Using Mnemonic
```bash
florad keys add <KEY_NAME> --recover
```
- `<KEY_NAME>`: Replace this with your key name.
- You will be prompted to enter your mnemonic to recover the key.

## List All Keys
```bash
florad keys list
```
- This command displays all keys currently stored in your wallet.

## Delete a Key
```bash
florad keys delete <KEY_NAME>
```
- `<KEY_NAME>`: Replace this with the name of the key you want to delete.
- You will be prompted for confirmation to delete the key.
