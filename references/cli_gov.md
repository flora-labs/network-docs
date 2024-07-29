# Governance

## Submit a Proposal
```bash
florad tx gov submit-proposal param-change <PROPOSAL_DEFINITION.JSON> \
  --from <KEY_NAME> \
  --chain-id <CHAIN_ID>
```
- `<KEY_NAME>`: Your key name for transaction authorization.
- `<PROPOSAL_DEFINITION.JSON>`: Content of the proposal defined as JSON file.
- `<CHAIN_ID>`: ID of the blockchain.	


## Deposit to a proposal
```bash
florad tx gov deposit 1 <AMOUNT>uflora \
  --from <KEY_NAME> \  
  --chain-id <CHAIN_ID>
```
- `<AMOUNT>`: Amount of tokens to deposit in proposal (`uflora`).
- `<KEY_NAME>`: Your key name for transaction authorization.	
- `<CHAIN_ID>`: ID of the blockchain.


## Vote on a Proposal
```bash
florad tx gov vote <PROPOSAL_ID> <VOTE_OPTION> \
  --from <KEY_NAME>
```
- `<PROPOSAL_ID>`: The ID of the proposal you want to vote on.
- `<VOTE_OPTION>`: Voting option (`yes`, `no`, `abstain`, `no_with_veto`).
- `<KEY_NAME>`: Your key name for transaction authorization.

## Query Proposals
```bash
florad query gov proposals
```
- Lists all proposals along with their statuses.
