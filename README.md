## TicTacToe solidity
A simple implementation of TicTacToe game in Solidity.
Following, a script to run in truffle console in order to play a demo match:

```solidity
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
