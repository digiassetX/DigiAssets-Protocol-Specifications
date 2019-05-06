# DigiAssets.net Public Test API
The DigiByte core developers provide a tesnet and mainnet API for developers to use when first getting started with DigiAssets. While we provide this to help people get started, we recommend companies, and services run their own infrastructure to keep DigiAssets as decentralized as possible. 

To set up and run your own API you need to run 4 things: [digibyted](https://github.com/digibyte/digibyte/releases), [digiassetsd](https://github.com/DigiByte-Core/digiassetsd), [DigiAssets Block Explorer](https://github.com/DigiByte-Core/DigiAssets-Block-Explorer) and [DigiAssets Metadata Server](https://github.com/DigiByte-Core/DigiAssets-Metadata-Server). You will also need to chose where and how to handle your metadata. We have used AWS buckets in testing, but you can use other services such as Azure blob storage.

# [Public API Docs](http://api.digiassets.net/docs/)
You can test the DigiAssets.net API and find more documentation here: http://api.digiassets.net/docs/

# DigiAssets API Calls:

### issue
```sh
issueAssetRequest {
issueAddress (string): Base58 public key address of asset issuer,
amount (integer): Amount of the asset to issue,
fee (integer): Mining fee for the transaction, in satoshi,
pubKeyReturnMultisigDust (string, optional): Encoded public key if you want to receive the multisig dust if multisig is needed for the metadata,
financeOutput (vout, optional): Use this vout as the first input, for the transaction,
financeOutputTxid (string, optional): txid containing the output used for finance,
reissueable (boolean, optional): Can the asset be reissued, in simple cases there is no need for mint tokens, the same key can resissue the asset,
aggregationPolicy (string, optional) = ['aggregatable' or 'dispersed']: Can assets be aggregated,
flags (flags, optional): Flags for this transaction,
divisibility (integer, optional): How divisible is the asset (the smallest transferable amount of an asset is 10^(-divisibility)),
transfer (array[transfer], optional): Where to transfer assets from the issuance,
rules (rules, optional): Section used only if the transaction is a reissueance trasaction,
metadata (metadata, optional): Additional data to be associated with the issuance transaction
}
vout {
value (integer): value in satoshi,
n (integer): ouput index,
scriptPubKey (scriptPubKey): scriptPubKey
}
scriptPubKey {
asm (string): asm,
hex (string): hex,
type (string): type of contract,
reqSigs (integer, optional): number of signatures,
addresses (array[string], optional): array of addresses
}
flags {
injectPreviousOutput (boolean, optional): If true will insert the pervious output into the input script so it can be used when signing
}
transfer {
address (string, optional): Address to transfer the asset to,
amount (integer): Amount of units of the asset to transfer,
pubKeys (array[string], optional): Send to a multisig adress instead of an address,
m (integer, optional): Number of signatures needed to reedeem the multisig
}
rules {
version (integer): version of the rule system,
fees (addressAssetValueList, optional): Array of fee itmes and locking items,
expiration (expirationItem, optional): Name of the category,
minters (array[mintersList], optional): Name of the category,
holders (array[holdersList], optional): Name of the category
}
addressAssetValueList {
items (array[addressAssetValue]): Array of SendAssetToAdress items,
locked (boolean): is the list locked
}
addressAssetValue {
address (string): Name of the category,
assetId (string): Name of the category,
value (number): Name of the category
}
expirationItem {
validUntil (integer): valid till block,
locked (boolean): Name of the category
}
mintersList {
address (string): Array of fee itmes and locking items,
locked (boolean): Name of the category
}
holdersList {
address (string): Array of fee itmes and locking items,
locked (boolean): Name of the category
}
metadata {
assetId (string, optional): assetId string,
assetName (string, optional): Name of the asset,
assetGenesis (string, optional): block + tx of the genisis for this asset,
issuer (string, optional): Name of the asset issuer,
description (string, optional): String that describes the asset,
urls (array[urlItem], optional): section used only if the transaction is a reissueance trasaction,
encryptions (array[encryptSection], optional): section used only if the transaction is a reissueance trasaction,
userData (json, optional): section used only if the transaction is a reissueance trasaction
}
urlItem {
name (string): Array of fee itmes and locking items,
url (string): Name of the category,
mimeType (string): mime type of data in that url,
dataHash (string, optional): hash of the data in that url
}
encryptSection {
key (string): the key inside userData we want to encrypt,
pubKey (string, optional): Public key we will use for the encryption (rsa pubkey),
format (string) = ['pem' or 'der']: Public key we will use for the encryption (rsa pubkey),
type (string) = ['pkcs1' or 'pkcs8']: Public key we will use for the encryption (rsa pubkey)
}
json {
}
```

### sendasset
```sh
sendAssetRequest {
fee (integer): Mining fee for the transaction, in satoshi,
pubKeyReturnMultisigDust (string, optional): Encoded public key if you want to receive the multisig dust if multisig is needed for the metadata,
from (array[string], optional): Adress to send the asset from,
sendutxo (array[string], optional): utxo to use for sending the asset itself,
financeOutput (vout, optional): use this vout as the first input, for the transaction,
financeOutputTxid (string, optional): txid containing the output used for finance,
to (array[transferWithAssetId]): Array of transferWithAssetId items,
flags (flags, optional): Flags for this transaction,
rules (rules, optional): section used only if the transaction is a reissueance trasaction,
metadata (metadata, optional): Additional data to be associated with the issuance transaction
}
vout {
value (integer): value in satoshi,
n (integer): ouput index,
scriptPubKey (scriptPubKey): scriptPubKey
}
scriptPubKey {
asm (string): asm,
hex (string): hex,
type (string): type of contract,
reqSigs (integer, optional): number of signatures,
addresses (array[string], optional): array of addresses
}
transferWithAssetId {
address (string, optional): Address to transfer the asset to,
amount (integer): Amount of units of the asset to transfer,
assetId (string): Id of the asset,
pubKeys (array[string], optional): Send to a multisig address instead of an address,
m (integer, optional): Number of signatures needed to reedeem the multisig
}
flags {
injectPreviousOutput (boolean, optional): If true will insert the pervious output into the input script so it can be used when signing
}
rules {
version (integer): version of the rule system,
fees (addressAssetValueList, optional): Array of fee itmes and locking items,
expiration (expirationItem, optional): Name of the category,
minters (array[mintersList], optional): Name of the category,
holders (array[holdersList], optional): Name of the category
}
addressAssetValueList {
items (array[addressAssetValue]): Array of SendAssetToAdress items,
locked (boolean): is the list locked
}
addressAssetValue {
address (string): Name of the category,
assetId (string): Name of the category,
value (number): Name of the category
}
expirationItem {
validUntil (integer): valid till block,
locked (boolean): Name of the category
}
mintersList {
address (string): Array of fee itmes and locking items,
locked (boolean): Name of the category
}
holdersList {
address (string): Array of fee itmes and locking items,
locked (boolean): Name of the category
}
metadata {
assetId (string, optional): assetId string,
assetName (string, optional): Name of the asset,
assetGenesis (string, optional): block + tx of the genisis for this asset,
issuer (string, optional): Name of the asset issuer,
description (string, optional): String that describes the asset,
urls (array[urlItem], optional): section used only if the transaction is a reissueance trasaction,
encryptions (array[encryptSection], optional): section used only if the transaction is a reissueance trasaction,
userData (json, optional): section used only if the transaction is a reissueance trasaction
}
urlItem {
name (string): Array of fee itmes and locking items,
url (string): Name of the category,
mimeType (string): mime type of data in that url,
dataHash (string, optional): hash of the data in that url
}
encryptSection {
key (string): the key inside userData we want to encrypt,
pubKey (string, optional): Public key we will use for the encryption (rsa pubkey),
format (string) = ['pem' or 'der']: Public key we will use for the encryption (rsa pubkey),
type (string) = ['pkcs1' or 'pkcs8']: Public key we will use for the encryption (rsa pubkey)
}
json {
}
```

### burnasset
```sh

```

# Mainnet URLs
```sh
api.digiassets.net/v3

explorerapi.digiassets.net
```

# Testnet URLs
```sh
testnetapi.digiassets.net/v3

testnetexplorerapi.digiassets.net
```