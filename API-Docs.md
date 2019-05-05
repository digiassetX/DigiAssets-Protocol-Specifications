# DigiAssets.net Public Test API
The DigiByte core developers provide a tesnet and mainnet API for developers to use when first getting started with DigiAssets. While we provide this to help people get started, we recommend companies, and services run their own infrastructure to keep DigiAssets as decentralized as possible. 

To set up and run your own API you need to run 4 things: [digibyted](https://github.com/digibyte/digibyte/releases), [digiassetsd](https://github.com/DigiByte-Core/digiassetsd), [DigiAssets Block Explorer](https://github.com/DigiByte-Core/DigiAssets-Block-Explorer) and [DigiAssets Metadata Server](https://github.com/DigiByte-Core/DigiAssets-Metadata-Server). You will also need to chose where and how to handle your metadata. We have used AWS buckets in testing, but you can use other services such as Azure blob storage.

Here are the main URLs for our public DigiAssets.net Api:

# Mainnet
api.digiassets.net/v3
explorerapi.digiassets.net

# Testnet
testnetapi.digiassets.net/v3
testnetexplorerapi.digiassets.net

You can find more info about the DigiAssets.net API here: http://api.digiassets.net/docs/