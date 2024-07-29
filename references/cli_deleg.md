# Delegations

## Delegate Tokens
```bash
florad tx staking delegate <VALIDATOR_OPERATOR_ADDRESS> <AMOUNT>uflora \
  --from <KEY_NAME> \
  --chain-id <CHAIN_ID>
```
- `<VALIDATOR_OPERATOR_ADDRESS>`: Address of the validator to delegate to.
- `<AMOUNT>`: Amount of tokens to delegate in microflora (`uflora`).
- `<KEY_NAME>`: Your key name for transaction authorization.
- `<CHAIN_ID>`: ID of the blockchain.

## Undelegate Tokens
```bash
florad tx staking undelegate <VALIDATOR_OPERATOR_ADDRESS> <AMOUNT>uflora \
  --from <KEY_NAME> \
  --chain-id <CHAIN_ID>
```
- `<VALIDATOR_OPERATOR_ADDRESS>`: Address of the validator from which you are undelegating.
- `<AMOUNT>`: Amount of tokens to undelegate in microflora (`uflora`).
- `<KEY_NAME>`: Your key name for transaction authorization.

## Redelegate Tokens
```bash
florad tx staking redelegate <SRC_VALIDATOR_OPERATOR_ADDRESS> <DST_VALIDATOR_OPERATOR_ADDRESS> <AMOUNT>uflora \
  --from <KEY_NAME> \
  --chain-id <CHAIN_ID>
```
- `<SRC_VALIDATOR_OPERATOR_ADDRESS>`: Source validator address.
- `<DST_VALIDATOR_OPERATOR_ADDRESS>`: Destination validator address.
- `<AMOUNT>`: Amount of tokens to redelegate in microflora (`uflora`).
