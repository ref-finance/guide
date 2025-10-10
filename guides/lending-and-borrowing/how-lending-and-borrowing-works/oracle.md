# Oracle

## Price Oracle <a href="#price-oracle" id="price-oracle"></a>

The platform uses a MakerDAO-inspired whitelisted oracle. The oracle currently has five independent operators and may be easily extended into a decentralized, self-sustainable network. For a price to be reported on-chain, the majority of oracles must propose the current price within a tight range.

Relevance of the price is less than 1 minute.

In the future, the DAO will consider adding other robust oracle solutions supported on NEAR, such as Flux.

The oracle code can be found here:

* [Smart Contract](https://github.com/NearDeFi/price-oracle)
* [Price Updater Bot](https://github.com/NearDeFi/near-price-oracle-bot) (system service)

### Pyth Oracle <a href="#pyth-oracle" id="pyth-oracle"></a>

The [Pyth Network](https://pyth.network/) is a first-party financial data oracle network that delivers low-latency price data for various assets to blockchains securely.

The Pyth protocol aggregates the data providers' inputs to produce a single aggregate price and confidence interval every 400ms for each price feed. This aggregation mechanism lives on an application-specific blockchain called Pythnet.

Pyth Network introduces a unique architecture called the Pull Oracle. With the Pull Oracle design, data users can “pull” or request a price update from the Pyth protocol when needed.

Learn more, refer to the [Pyth documentation](https://docs.pyth.network/home).\
