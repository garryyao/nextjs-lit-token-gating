# Next.js Lit Protocol Token Gating Example

This minimal example demonstrates how to implement token gating in a Decentralized Application (dApp) using [Lit Protocol](https://www.litprotocol.com/) and Next.js.

## Features

- Token gates the `/protected` page using Lit Protocol's access control conditions
- Verifies if the user's wallet address matches a specific address on a blockchain network
- Issues a signed JWT for cross-dApp verification

## Prerequisites

- A crypto wallet (e.g., MetaMask)
- Node.js v18 or later

## Quick Start

1. Clone and install dependencies:

```sh
cd nextjs-lit-token-gating

npm install
```

2. Update the [`accessControlConditions`](./pages/index.js#L11) with the contract address of the NFT you'd like to use:

```javascript
const accessControlConditions = [
  {
    contractAddress: '',
    standardContractType: '',
    chain: '<your_network_name>',
    method: '',
    parameters: [
      ':userAddress',
    ],
    returnValueTest: {
      comparator: '=',
      value: '<your_wallet_address>'
    }
  }
]
```
You can also try to use access control conditions using any valid conditions that [Lit supports](https://developer.litprotocol.com/sdk/access-control/condition-types/unified-access-control-conditions).

3. Start the app

```sh
npm run dev
```
Open http://localhost:3000, click on the **Connect** button to authenticate, which will prompt you to connect your wallet.

Once logging in with your wallet, you shall be able to see access granted and receive a token.
