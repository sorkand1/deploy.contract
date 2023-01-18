
<b>Step 1</b> : Add Ethereum A1 and Taiko A1 networks to Metamask [here](https://taiko.xyz/docs/alpha-1-testnet/configure-wallet)

<b>Step 2</b> : Ask for coins at the faucet [here](https://l2faucet.a1.taiko.xyz/)

To create a smart contract, we will use the service [remix.ethereum.org](https://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.7+commit.e28d00a7.js)

<b> Click New File > </b> and call it, for example, a <b> r1m.sol </b> it is important that the ending is <b>.sol</b> and paste the contract address below 

```
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;


contract R1M{

    address public owner;
    mapping (address => uint) public payments;

    constructor() {
        owner = msg.sender;
    }

    function Donate() public payable {
        payments[msg.sender] = msg.value;
    }

    function MoneyBack() public {
        address payable _to = payable(owner);
        address _thisContract = address(this);
        _to.transfer(_thisContract.balance);
    }
}
```

And press <b>CONTROL+S</b> to preserve 

Click on <b>SOLIDITY COMPILER</b>change COMPILE version for 0.8.0 and press <b>compile r1m.sol</b>

Click on <b>DEPLOY & RUN TRANSACTIONS</b>change ENVIRONMENT for <b>Injected provider Metamask</b>change chain in metamask for <b>Taiko A1</b>and press <b>Deploy</b>
 
Click on <b>DEPLOYED CONTRACTS</b>click on <b>Donate</b> signing the transaction and click on <b>MoneyBack</b> signing the transaction 

You can check transactions in the Metamask wallet or in the [Explorer](https://l2explorer.a1.taiko.xyz/)
