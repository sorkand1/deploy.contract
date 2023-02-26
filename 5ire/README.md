<b>creating a smart contract (Native chain)</b>

<b>Step 1</b> : Download the wallet[here](https://explorer.5ire.network/) turn on Developer Mode in you browser, and setup wallet

<b>Step 2</b> : Ask for coins at the faucet [here](https://explorer.5ire.network/faucet)

<b>Step 3</b> : Clone Git Repository

<b> Next, we need to download the software and install it on your PC</b> [Visual Studio Code](https://code.visualstudio.com/) and [Node JS](https://nodejs.org/uk/download/)

<b> Click Terminal > New Terminal </b> and download the <b>git</b>, the command is below 

```
winget install --id Git.Git -e --source winget
```
Next, open a new window <b>File > New Window > Clone Git Repository </b> and clone repository

```
https://github.com/5ire-tech/wasm-contract-deployment
```
and open a cloned repository, switching a terminal in <b>cmd</b>

<b>Step 1</b> 

```
npm i
```
<b>Open <b>deploy.js</b>and paste <b>privat_key</b> in this file and press <b>CONTROL+S</b>

<b>Step 3</b> deploy 
```
node deploy.js
```
<H1>Creating a smart contract (EVM)</H1>

<b>Step 1</b> : Import you Ethereum private key in metamask

<b>Step 2</b> : Ask for coins at the faucet [here](https://explorer.5ire.network/faucet)

To create a smart contract, we will use the service [remix.ethereum.org](https://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.7+commit.e28d00a7.js)

<b> Click New File > </b> and call it, for example, a <b> r1m.sol </b> it is important that the ending is <b>.sol</b> and paste the contract address below 

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;
 
// https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v3.0.0/contracts/token/ERC20/IERC20.sol
interface IERC20 {
   function totalSupply() external view returns (uint);
 
   function balanceOf(address account) external view returns (uint);
 
   function transfer(address recipient, uint amount) external returns (bool);
 
   function allowance(address owner, address spender) external view returns (uint);
 
   function approve(address spender, uint amount) external returns (bool);
 
   function transferFrom(
       address sender,
       address recipient,
       uint amount
   ) external returns (bool);
 
   event Transfer(address indexed from, address indexed to, uint value);
   event Approval(address indexed owner, address indexed spender, uint value);
}
 
 
 
contract ERC20 is IERC20 {
   uint public totalSupply;
   mapping(address => uint) public balanceOf;
   mapping(address => mapping(address => uint)) public allowance;
   string public name = "Solidity by Example";
   string public symbol = "SOLBYEX";
   uint8 public decimals = 18;
 
   function transfer(address recipient, uint amount) external returns (bool) {
       balanceOf[msg.sender] -= amount;
       balanceOf[recipient] += amount;
       emit Transfer(msg.sender, recipient, amount);
       return true;
   }
 
   function approve(address spender, uint amount) external returns (bool) {
       allowance[msg.sender][spender] = amount;
       emit Approval(msg.sender, spender, amount);
       return true;
   }
 
   function transferFrom(
       address sender,
       address recipient,
       uint amount
   ) external returns (bool) {
       allowance[sender][msg.sender] -= amount;
       balanceOf[sender] -= amount;
       balanceOf[recipient] += amount;
       emit Transfer(sender, recipient, amount);
       return true;
   }
 
   function mint(uint amount) external {
       balanceOf[msg.sender] += amount;
       totalSupply += amount;
       emit Transfer(address(0), msg.sender, amount);
   }
 
   function burn(uint amount) external {
       balanceOf[msg.sender] -= amount;
       totalSupply -= amount;
       emit Transfer(msg.sender, address(0), amount);
   }
}
```

And press <b>CONTROL+S</b> to preserve 

Click on <b>SOLIDITY COMPILER</b>change COMPILE version for 0.8.18 and press <b>compile r1m.sol</b>

Click on <b>DEPLOY & RUN TRANSACTIONS</b>change ENVIRONMENT for <b>Injected provider Metamask</b>change chain in metamask for <b>5ire</b>and press <b>Deploy</b>

You can check transactions in the Metamask wallet 
