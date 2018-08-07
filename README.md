
# A Simple ERC-721 Example

What is it?

![](https://cdn-images-1.medium.com/max/2000/0*jr7S0JF8XiousKKz.png)

ERC-721 tokens are a hot topic today with the advent of [crypto kitties](https://www.cryptokitties.co/) and a host of other digital collectibles spawned by its success. The [ERC-721 standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) has gone through a couple iterations and is more or less in place now, so expect more and more players to enter this space. The basic premise of these [non-fungible tokens](https://en.wikipedia.org/wiki/Non-Fungible_Tokens) is that each token is unique and therefore cannot be exchanged on a 1:1 basis like an ERC20 token may be. There are many use cases where a unique tangible or digital asset may represented by these ERC-721 tokens, such as real estate, art, precious stones, etc. Actually, the digital collectible use case is probably the lowest market value use case of them all.

### **Purpose of this article**

This article will attempt to create an ERC-721 in its simplest useful form using the [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-solidity/tree/master/contracts/token/ERC721) implementation of the [ERC-21 standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md). I would recommend looking at the standard linked above in order to familiarize yourself with the requirements as they can be sometimes be hidden in the excellent OpenZeppelin implementations. There is also a fantastic article written [here](https://medium.com/blockchannel/walking-through-the-erc721-full-implementation-72ad72735f3c) that describes in-depth the ERC-721 spec.

### Setup the project

Make sure that you have node, npm and truffle installed

    mkdir erc721 && cd erc721 && truffle init

Replace the *truffle.js* content with the following:

<iframe src="https://medium.com/media/f3ef2f3c60d4dac9bad5fe59ae3f8564" frameborder=0></iframe>

Install [Ganache](http://truffleframework.com/ganache/) and make sure it is running on 8545

Compile and Migrate

    truffle compile
    truffle migrate

Init the folder as an npm project

    npm init

Install zeppelin dependency

    npm install zeppelin-solidity

### The Token

Add the following to /contracts as *MyERC721.sol*

<iframe src="https://medium.com/media/9d1b82940c835e700f785efd4dbb786d" frameborder=0></iframe>

Add the following migration to /migrations as *2_erc721_migration.js*

<iframe src="https://medium.com/media/7d0a5b5eaaab6c02c2f9f1243b70679c" frameborder=0></iframe>

Run the migrate script and verify that it deploys without errors

    Marks-MacBook-Pro:erc721 markmathis$ truffle migrate
    Using network 'development'.

    Running migration: 2_erc721_migration.js
    Deploying MyERC721...
    ...
    0x25c26fd5b79b6328bee75bd34d78b37ff9389aad2d487600d46595adf0ee398d
    MyERC721: 0x6d9b92dfaf3cc3ae2e45b37b584f52f23bc03085
    Saving successful migration to network...
    ...
    0x5c147afb3f4c2d225ef3b4cabcd7b9d3b5e4cbab88617fa150b061b85eb4cc0a
    Saving artifacts...

### Test it out

Install test libraries

    npm install chai --save-dev
    npm install chai-as-promised --save-dev
    npm install babel-preset-es2015 --save-dev
    npm install babel-register --save-dev
    npm install babel-polyfill --save-dev

Add *.babelrc *to project root

    {
      "presets": ["babel-preset-es2015"]
    }

Add *erc721.spec.js* to /test

<iframe src="https://medium.com/media/b9076ee98f1179a46ac48c5f523e3a0b" frameborder=0></iframe>

Run the test from the project root

    truffle test

![](https://cdn-images-1.medium.com/max/3236/1*tZ9h1i5oaWrD8ISiGH5L8w.png)

### Addendum

Pretty much all of the regular ERC20 functions are available in the ERC721 contracts. You can approve a third party to spend your token, burn tokens, etc. The functionality is the same, but the inputs and what happens under the covers is a bit more complex. There are a couple ERC721 methods that are not discussed in this article that are worth independent study as well

* safeTransferFrom

* isApprovedForAll

* setApprovedForAll

### Summary

Let’s recap what we learned in this article. First, we setup the project with truffle and imported our dependencies including the world class smart contract library, **OpenZeppelin. **Next, we coded our ERC721 token using the OpenZeppelin — *ERC721Token *template. We ran through a few checks to make sure our contract was valid and then we setup a mocha test to test our assertions. Our solidity code is deceptively simple and I would recommend a deeper dive into the ERC721 standard and the OpenZeppelin implementation. We accomplished our purpose in this article by creating a simple ERC721 token and you should be in a good place to continue your journey in learning this new token type. Even though this token was not ‘fungeable’ — I hope you still had ‘fun’ :)

*Full project source is available* — [here](https://github.com/cipherzzz/erc721)
