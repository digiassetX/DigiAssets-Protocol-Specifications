# DigiAssets.net Public Test API
The DigiByte core developers provide a tesnet and mainnet API for developers to use when first getting started with DigiAssets. While we provide this to help people get started, we recommend companies, and services run their own infrastructure to keep DigiAssets as decentralized as possible. 

To set up and run your own API you need to run 4 things: [digibyted](https://github.com/digibyte/digibyte/releases), [digiassetsd](https://github.com/DigiByte-Core/digiassetsd), [DigiAssets Block Explorer](https://github.com/DigiByte-Core/DigiAssets-Block-Explorer) and [DigiAssets Metadata Server](https://github.com/DigiByte-Core/DigiAssets-Metadata-Server). You will also need to chose where and how to handle your metadata. We have used AWS buckets in testing, but you can use other services such as Azure blob storage.

# [Public API Docs](http://api.digiassets.net/docs/)
You can test the DigiAssets.net API and find more documentation here: http://api.digiassets.net/docs/

# DigiAssets API Calls:

### issue
### sendasset
### burnasset
### broadcast
### assetmetadata
### addressinfo
### stakeholders

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