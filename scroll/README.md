
<b>Step 1</b> : Add L1 Testnet and Scroll L2 networks to Metamask [here](https://scroll.io/prealpha)

<b>Step 2</b> : Ask for coins at the faucet [here](https://scroll.io/prealpha/faucet)

<b>Step 3</b> : Go to Bridge and transfer some Ethereum from the network L1 Testnet in Scroll L2

<b> Next, we need to download the software and install it on your PC</b> [Visual Studio Code](https://code.visualstudio.com/) and [Node JS](https://nodejs.org/uk/download/)

<b> Click Terminal > New Terminal </b> and download the <b>git</b>, the command is below 

```
winget install --id Git.Git -e --source winget
```
Next, open a new window <b>File > New Window > Clone Git Repository </b> and clone repository

```
https://github.com/scroll-tech/scroll-contract-deploy-demo.git
```
and open a cloned repository, switching a terminal in <b>cmd</b>

<b>Step 1</b> Install yarn

```
yarn install
```
<b>Step 2</b> Make a copy of the file <b>.env.example</b> and change the name of the copied file to <b>.env</b> and paste <b>privat_key</b> in this file and press <b>CONTROL+S</b>

<b>Step 3</b> Do Compine
```
yarn compile
```

<b>Step 4</b> Do Deploy
```
yarn deploy:scrollTestnet
```

<b>Step 4</b> Do Test
```
yarn test
```
