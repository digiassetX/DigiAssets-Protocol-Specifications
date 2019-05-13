# Overview
## DigiByte
Founded in early 2014, DigiByte is the fastest, most decentralized and secure UTXO blockchain in the world today. In what follows we will use the customary notation of referring to the DigiByte network/protocol as **DigiByte** (Camel-case) and to the units of currency flowing in the DigiByte network as **DigiBytes**.

By design, DigiBytes have several incredibly desirable technical attributes
* Fixed supply
* Non-counterfeitable
* Divisible
* Easily transportable

On top of that, DigiByte is highly decentralized. Decentralization adds an extra layer of robustness because the DigiByte network has no single point of failure. A by-product of this is also that DigiByte is permissionless, in that there is no single entity to ask for permission to use / send / receive DigiBytes or the DigiByte network.

All DigiByte transactions are publicly available on a ledger known as “The Blockchain” and quickly become practically immutable.

## DigiAssets

While originally designed to be a cryptocurrency, DigiByte supports a limited scripting language that can be used to store metadata on the blockchain. DigiAssets is a concept that allows attaching metadata to DigiByte transactions and leveraging the DigiByte infrastructure for issuing and trading immutable digital assets that can represent real world value. The value of such digital assets is tied to a real-world promise by the asset issuers that they are willing to redeem those digital tokens for something of value in the real world. 

Digital assets on top of the DigiByte Blockchain can be used to issue Financial assets (securities like shares, commodities like Gold or new currencies), prove ownership (A digital key to a house or a car, a concert ticket), store information (Documents, Certificates) or create smart contracts.

The advantage given by using the blockchain as the backbone for such asset manipulation is that one can rely on the blockchain’s transparency, immutability, ease of transfer and non-counterfeitability to transfer and trade such digital tokens with unprecedented security and ease.



# The DigiAssets Protocol
This document describes the DigiAssets protocol specification for issuing and transacting digital assets on top of the DigiByte Blockchain.

This Document consists of two main parts:
## 1. The [DigiAsset Scheme](DigiAsset%20Scheme)
The DigiAsset scheme describes the encoding used to encode/decode the DigiAssets data that is stored in a DigiByte transaction after the OP_RETURN operator (and sometimes in one additional multisignature output). This DigiAsset scheme is optimized for robust functionality by inserting the most data within the current size constraints of the OP_RETURN operator (80 Bytes).

## 2. [Asset Metadata](Metadata) and the [Rule engine](Rules)
This document introduces the first specification for handling metadata for digital assets.
Because of the 80 Bytes limit of the OP_RETURN field, any metadata that is attached to a transaction is hashed and stored in torrents to allow decentralized access to the information.
By hashing the metadata for every transaction, DigiAssets actually expands dramatically the basic DigiByte functionality by allowing to insert rules that exist outside the blockchain and can be publicly accessed via torrents and verified against a specific transaction thus creating a rule engine with basic smart contract functionality.