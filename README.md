<h1 align="center">Welcome to Lending Swap 👋</h1>
<p>
  <img src="https://img.shields.io/badge/version-1.0-blue.svg?cacheSeconds=2592000" />
</p>
<div float: left;
  width: 33.33%;
  padding: 5px;>
<image src='./readme-images/Ethereum-icon.png'  width='10%'/>
<image src='./readme-images/aave.png'  width='10%'/>
<image src='./readme-images/band-logo.png'  width='10%'/>
<image src='./readme-images/harmony.png'  width='35%'/>
</div>

## Introduction

Lending Swap is an application used to swap atoms between tokens, native tokens from Ethereum to Harmony and vice versa.

Between two bridges of Ethereum - Harmony, there are 2 relayers to be able to mint corresponding tokens when swapping between the two platform.

There will be validators at each bridge to verify the atomic swaps, when **75%** consensus is reached, the transaction will be executed by the relayer.

In order to be able to transfer the equivalent value of tokens, for example **ETH -> ONE**, **KNC (ERC20) -> WETH (HRC20)**, we use price data taken from **Band Oracle**.

## Architecture

### Sequence Diagram

- Ethereum -> Harmony

<image src='./readme-images/ethtohmy.png' />

- Harmony -> Ethereum

<image src='./readme-images/hmytoeth.png' />

### Lending

On the ethereum side, when a user performs transactions to swap to Harmony, the token amount will be locked and then staked in **AAVE** (has been upgraded to version 2). The yield obtained from the lending will be returned to the validators involved in verifying the swap transactions.

### Swap

There are 2 BridgeBank contracts on 2 sides that are responsible for receiving transactions to swap tokens and emit out events for the other contract. Contract on that side will be based on the price data taken from the **Band Protocol** to be able to unlock the corresponding amount of tokens. Before being unlocked, the transaction will have to get **75% validator** approval
