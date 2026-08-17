# ZK-Shielded Intent Protocol
> A private settlement engine proving trade constraints without revealing them.

## Contract Address
| Network | Address |
|----------|----------------------------------|
| Preview | N/A |
| Preprod | [PASTE_ADDRESS_HERE] |

## What This Does
This contract keeps a public interaction count that can only be incremented if a user cryptographically proves their hidden value meets a specific threshold. 

## Privacy Model
- **What is PUBLIC (on-chain, visible to anyone):**
  - `interactionCount` — the total number of verified interactions (`Counter`)
- **What is PRIVATE (private witness, never on-chain):**
  - `secretValue()` — the user's hidden threshold value (`Uint<32>`)
  - `stepAmount()` — the amount to increment the counter (`Uint<16>`)
- **What the user PROVES without revealing:**
  - That their private `secretValue()` is greater than or equal to 100.
  - The zero-knowledge circuit enforces this rule locally before submitting anything.

`disclose()` is used deliberately to reveal only the `stepAmount()` when incrementing the public counter, while keeping the core secret value entirely hidden.

## Tech Stack
- Midnight network (Preprod)
- Compact language (compiler 0.31.1)
- Node.js v22
- Docker (proof-server)

## Prerequisites
- Node.js v22 or newer
- Docker
- Midnight Compact Compiler

## Setup
```bash
git clone <your-repo-url>
cd zk-shield
npm install
npm run compile
Pending (Midnight Preprod RPC nodes failing to sync locally - testnet outage. Contract compiles successfully.)
