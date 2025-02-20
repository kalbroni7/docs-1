---
title: dex.trades
description: dex.trades aggregates data across multiple DEX platforms into one simple table.
---

Decentralized exchanges are the beating heart of the DeFi industry. You can swap any [ERC-20](token-standards/erc-20.md) token for any ERC-20 token through the magic of smart contracts.

The problem here: there are so many decentralized exchanges out there that it's hardly possible for any single person to work with the smart contract data for all of them.

That's why we created [dex.trades](https://dune.com/spellbook#!/model/model.spellbook.dex_trades).

This table standardizes and normalizes the trading data across virtually all relevant decentralized exchanges. This in turn allows you to easily query for trading data for your favorite tokens without having to deal with all of the different DEX smart contracts yourself.

The scripts that generate the table dex.trades can be found in this [public github](https://github.com/duneanalytics/spellbook/tree/master/ethereum/dex) repo.

## Column Data

| Column name | Data type | Description |
| - | :-: | - |
| `block_time` | _timestamptz_ | The timestamp of the block that included this transaction |
| `token_a_symbol` | _string_ | The symbol of one of the two tokens that got traded |
| `token_b_symbol` | _string_ | The symbol of one of the two tokens that got traded |
| `token_a_amount` | _numeric_ | The amount of token A that got traded |
| `token_b_amount` | _numeric_ | The amount of token B that got traded |
| `project` | _string_ | The dex on which this trade was executed |
| `version` | _string_ | Which version of the dex got used? |
| `category` | _string_ | Is this project and aggregator or a decentralized exchange? |
| `trader_a` | _bytea_ | Which contract called the dex contract? |
| `trader_b` | _bytea_ | In some special cases there actually is a counter party to transactions, this party will get displayed here if applicable |
| `token_a_amount_raw` | _numeric_ | The raw amount of token A that got traded |
| `token_b_amount_raw` | _numeric_ | The raw amount of token B that got traded |
| `usd_amount` | _numeric_ | The USD value of this trade |
| `token_a_address` | _bytea_ | The ERC-20 token contract address of token A |
| `token_b_address` | _bytea_ | The ERC-20 token contract address of token B |
| `exchange_contract_address` | _bytea_ | The address of the decentralized exchange contract that made this trade possible |
| `tx_hash` | _bytea_ | The hash of the transaction that contained this trade |
| `tx_from` | _bytea_ | Which address initiated this transaction? |
| `tx_to` | _bytea_ | What was the first smart contract that got called during this tx? |
| `trace_address` | _ARRAY_ | Which position in the graph tree does the execution of the trade have? |
| `evt_index` | _integer_ | This logs index position in the block (cumulative amount of logs ordered by execution) |
| `trade_id` | _integer_ | Just for database magic |
