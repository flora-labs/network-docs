# Validator deployment

How to check current validators list
(link to explorer as well as to CLI reference)

## Creating identity for validator
Information about Keybase and how to create profile for validator, so it can present logotype in most explorers


## Creating keys for validator



## Turning node into validator

```bash
florad tx staking create-validator \
  --chain-id="CHAIN_NAME" \
  --commission-rate=0.05 \
  --commission-max-rate=0.3 \
  --commission-max-change-rate=0.1 \
  --min-self-delegation="1" \
  --amount=1000000utoken  \
  --pubkey $(florad tendermint show-validator) \
  --website "https://validator.website.url"   \
  --identity KEYBASE_IDENTITY   \
  --details "Short bio"   \
  --security-contact "contact@validator.domain"   \
  --from=validator_wallet \
  --gas="auto" \
  --gas-adjustment 1.1 \
  --node http://localhost:26677 \
  --fees 5000utoken
```

