# deltaSwap
(Built for the Gitcoin Concordium Hackathon)

### Mainnet Address: ```3yMZoZpVhgwrm8WSnhuvggeEQQQaKkxjTyiTiZ6pMrfMChuvdh```

[Check it out](https://delta-swap.vercel.app)

### Deltaswap is a Uniswap V1 inspired decentralized exchange and liquidity staking platform, and it uses a constant function market maker

[![](https://s9.gifyu.com/images/image55172a3659d42b9d.png)](https://gifyu.com/image/S7H4c)
[![](https://s3.gifyu.com/images/image7689320c50921740.png)](https://gifyu.com/image/S7H4i)
[![](https://s3.gifyu.com/images/imageb4180549bbad9773.png)](https://gifyu.com/image/S7H4D)
[![](https://s9.gifyu.com/images/image4f8abda9469f0a21.png)](https://gifyu.com/image/S7H4e)

## Features
- Slick UI
- Any CIS2 Token id is supported because the contract uses TokenIdVec
- Liquidity Pool explorer where you can add or remove liquidity
- Swap interface that lets you search and select the asset you want to trade
- Realtime prediction of how much token you will recieve
- Seamless user experience
- Named after delta wings

## Tech Stack
- SvelteKit
- Vite
- Vercel
- TailwindCSS
- DaisyUI
- TypeScript

## Issues I ran into while working on this project
- I needed to fork the @concordium/web-sdk npm package because by default it wasn't compatible with vite, check it out here [concordium-web-sdk-vite](https://www.npmjs.com/package/concordium-web-sdk-vite)
- I tried including age verification in this project but unfortunately i couldn't find a way to do it with the smart contract, and since client side authentication would be pointless in a dapp where anyone can interact with the contract without using my fronted, i opted not include this feature
- I couldn't make a smart contract which supports all TokenAmounts so this one uses TokenAmountU64, of course it can be easily modified to work with a different amount
- I tried to get the block time in the contract, but the method: ```get_slot_time()``` that is supposed to do this is unsafe and didn't work for me
- In the web-sdk I couldn't find a way to get the schema that can be embedded into the smart contract

## Personal Comment:
While there were a lot of issues which caused me to run out of time to perfect this project, I still enjoyed this hackathon and see the potential in Concordium, I hope you guys put in the time to perfect it and make it more usable for developers

## How to get running

Lets start with the contract

1. Ensure you have all the tools for developing Concordium smart contracts and you have set up your concordium-client
2. ```cd contract```
3. ```cargo concordium build --schema-base64-out "./base64_schema.b64" --out ./exchange.wasm.v1```
4. ```concordium-client module deploy exchange.wasm.v1 --sender test --grpc-ip node.testnet.concordium.com --grpc-port 10000```
5. Copy your deployed module address

And now comes the frontend

1. ```cd frontend```
2. Paste the module address into ```src/lib/Constants.ts```
3. ```yarn```
4. ```yarn dev``` or ```yarn build```

Congrats you made it!


## Disclaimer
- This is just a prototype and shouldn't be used in a production environment
- Only works with TokenAmountU64
- There are a lot of visual bugs in the frontend, since @concordium/web-sdk kept breaking and i had to rewrite my code many times

