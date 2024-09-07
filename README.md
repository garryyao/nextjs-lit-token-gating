This is a minimal example illustrate how a Decentralized Applications (dApps) can token-gate a Next.js page using [Lit Protocol](https://www.litprotocol.com/) using their web sdk `@lit-protocol/lit-node-client`.   


This token gates a `/protected` page with access control conditions to see:
 - if the user's wallet address matches a specific user on a blockchain network.

The app then issues a signed JWT which can be later verified by any other dApps through the protocol.   

To get this example working, you will need to set up a crypto wallet if you don't have one. Google "how to get a blockchain
wallet". 

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
