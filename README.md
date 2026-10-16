# Pharos Read Contract State

## Overview

This project reads publicly accessible state values from a USDC token contract on the Pharos Atlantic Testnet.

## Network Details

* Network: Pharos Atlantic Testnet
* Chain ID: 688689
* Contract Address: `0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B`
* Block Number: `31508327`

## Contract Values

| Method          | Result          |
| --------------- | --------------- |
| `name()`        | USDC            |
| `symbol()`      | USDC            |
| `decimals()`    | 6               |
| `totalSupply()` | 100108137767829 |

The raw total supply is approximately 100,108.14 USDC after applying 6 decimals.

## How to Run

The contract state was read using the Pharos Atlantic Testnet RPC endpoint and the `cast call` tool.

Example commands:

```bash
cast call 0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B "name()(string)" --rpc-url https://atlantic.dplabs-internal.com

cast call 0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B "symbol()(string)" --rpc-url https://atlantic.dplabs-internal.com

cast call 0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B "decimals()(uint8)" --rpc-url https://atlantic.dplabs-internal.com

cast call 0xcfC8330f4BCAB529c625D12781b1C19466A9Fc8B "totalSupply()(uint256)" --rpc-url https://atlantic.dplabs-internal.com
```

## Sample Output

```text
Network: Pharos Atlantic Testnet
Block Number: 31508327
Token Name: USDC
Token Symbol: USDC
Token Decimals: 6
Raw Total Supply: 100108137767829
Human-Readable Total Supply: approximately 100108.14 USDC
```

## Notes

The values above are from a previous read and may change. Re-run the calls to obtain current results.

**Important:** This documents direct RPC reads using `cast call`. Chain MCP execution must be verified separately to satisfy the task requirement.

