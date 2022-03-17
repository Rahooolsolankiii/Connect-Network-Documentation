# Quick Guide

## Intro

Connect Network blockchain is called the Quore, which is a high-performance, highly scalable, customizable, and secure smart-contract platform. The Quore is permissionless, decentralized, and open-source.

**HBFT consensus algorithm:** is asynchronous, leaderless, Byzantine Fault-Tolerant, to achieve instant transaction finality. The Connect Network testnet has served more than 40M transactions with a daily growth of more than 500k transactions.

**Bonsai: From a Forest of Tries to a Bonsai Trie**

The Quore uses **Bunsai** \*\*\*\* fıle format, which can dramatically decrease the size of data storage space needed for the blockchain data.

{% hint style="info" %}
Connect Network's **total supply is a fixed 6,000,000 coins.**
{% endhint %}

Partners and integrations: soon

Connect Network community: soon

## **Join Enter network**

### Connect Network mainnet

Explorer: NA

Wallet: NA

RPC: NA

### Connect Network testnet

Explorer: NA

Wallet: NA

RPC: NA

### MetaMask

Connect to Enter mainnet: NA

Connect to Enter testnet: NA

The best way to interact with our API is to use one of our official libraries:

## Deploy Smart Contracts

PUBLIC API ENDPOINTS

**Multi-chain**

**Bridges - Under development, contributions welcome**

Spooky Bridge : Connect Network <> ETH/BSC

Ren:

Anyswap: Connect Network <> ETH, BSC, Polygon

Xpollinate: Connect Network <> BSC,xDAI, Polygon

Evodefi: Connect Network <> BSC, Polygon

**Useful links**

Careers



{% tabs %}
{% tab title="curl" %}
```
curl https://api.myapi.com/v1/pet  
    -u YOUR_API_KEY:  
    -d name='Wilson'  
    -d species='dog'  
    -d owner_id='sha7891bikojbkreuy'  
```
{% endtab %}

{% tab title="Node" %}
```javascript
// require the myapi module and set it up with your API key
const myapi = require('myapi')(YOUR_API_KEY);

const newPet = away myapi.pet.create({
    name: 'Wilson',
    owner_id: 'sha7891bikojbkreuy',
    species: 'Dog',
    breed: 'Golden Retriever',
})
```
{% endtab %}

{% tab title="Python" %}
```python
// Set your API key before making the request
myapi.api_key = YOUR_API_KEY

myapi.Pet.create(
    name='Wilson',
    owner_id='sha7891bikojbkreuy',
    species='Dog',
    breed='Golden Retriever',
)
```
{% endtab %}
{% endtabs %}
