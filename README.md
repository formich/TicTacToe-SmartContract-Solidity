## TicTacToe SmartConstract Solidity
A simple implementation of TicTacToe SmartContract game in [Solidity](https://solidity.readthedocs.io/en/develop/).

Features:
 - The game allows players to bet Ether on a TicTacToe Match, hoster and joiner has to bet the same amount of money;
 - The winner automatically gets the pot;
 - If the game is drawn then the pot is equally splitted;
 - The players are enforced to finish the match. So if one decide to leave, after 10 minutes other player can reclaim the whole pot;

 ### Install and Run

 In order to install and run this contract I really encourage you to install **[Truffle](https://github.com/trufflesuite/truffle)** and **[Ganache](https://github.com/trufflesuite/ganache)**. They make your life a lot easier, trust me.

 Once you've installed both of them , all you have to do is to start Ganache and keep it running in background, it will build a personal blockchain for you. You should see an interface like that:

 ![ganache interface](https://i.imgur.com/Ssochrq.png)

 Now you need to clone the repo into your local machine and from a terminal move inside the folder downloaded and execute the command
 ```bash
truffle compile && truffle migrate --reset
 ```
 It compiles and deploy the smart contract on your personal block chain!

 At this point you need to access the truffle console to interact directly with the contract, so you just have to type:
 ```bash
truffle console
 ```

So finally running the following steps you will instantiate the contract and play a demo match:

```javascript
// Create variables for two players
var accounts = web3.eth.accounts;
var host = accounts[0];
var opposition = accounts[1];

//  Instantiate contract from blockchain
var ttt = TicTacToe.at(TicTacToe.address);

// Make two players bet 10 Ether
ttt.start({from: host, value: web3.toWei("10", "ether")});
ttt.join(host, {from: opposition, value: web3.toWei("10", "ether")});

// Play some moves in order to finish the Match
//[X,X,X]
//[O,O,-]
//[-,-,-]
ttt.play(host, 0, 0, {from: opposition});
ttt.play(host, 1, 0, {from: host});
ttt.play(host, 0, 1, {from: opposition});
ttt.play(host, 1, 1, {from: host});
ttt.play(host, 0, 2, {from: opposition});
```
