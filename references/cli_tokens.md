# Operations on Tokens - Managing Tokens

## Send Tokens
```bash
florad tx bank send <FROM_KEY_NAME> <TO_ADDRESS> <AMOUNT>uflora \
  --from <KEY_NAME> \
  --chain-id <CHAIN_ID>
```
- `<FROM_KEY_NAME>`: Your key name for sending tokens.
- `<TO_ADDRESS>`: Recipient's address.
- `<AMOUNT>`: Amount to send in microflora (`uflora`).
- `<KEY_NAME>`: Your key name for transaction authorization.	
- `<CHAIN_ID>`: ID of the blockchain.

## Query Account Balance
```bash
florad query bank balances <address>
```
- `<address>`: The address to query balances for.
