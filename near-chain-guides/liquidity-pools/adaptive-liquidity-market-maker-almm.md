# Adaptive Liquidity Market Maker (ALMM)

Adaptive Liquidity Market Maker (ALMM) aim to enhance the trading experience by providing minimal swap price impact on volatile pools.

These pools are seeded with one volatile and one stable asset or two volatile assets but they employ the [Stableswap AMM](https://guide.ref.finance/products/overview/pooling#stablepool) instead of the Constant Product one. This choice enables traders to achieve an unparalleled efficiency as they can swap one asset for another at a 1:1 dollar ratio with little to no price impact.

In standard market conditions, ALMM are expected to gather a much higher trading volume than their standard counterparts.

#### ALMM Example <a href="#gitbookdegenpool-example" id="gitbookdegenpool-example"></a>

Assume there are two XYZ/USDC pools. One uses the Constand Product AMM and the other, the ALMM, uses the Stableswap AMM. Assume the pool TVL is $ 2 mln and that XYZ trades at 10 USDC.

A trader that wants to swap 50,000 USDC for XYZ would receive 4,762 XYZ by swapping in the standard pools and approximately 5,000 XYZ by swapping in the ALMMM. The higher swap efficiency of the ALMM amounts to 5% (5,000 / 4,762 -1 ) in this specific case, without considering swap fees.

#### ALMM Risk factors <a href="#gitbookdegenpool-riskfactors" id="gitbookdegenpool-riskfactors"></a>

Liquidity providers (LPs) that deposit capital in ALMM must be aware of the following risk factors:

* **Impermanent loss:** ALMM can expose LPs to a much higher impermanent loss compared to standard pools. This is because allowing traders to swap at a 1:1 dollar ratio could quickly deplete liquidity of either asset in case of large trading volume.
* **Oracle risk**: ALMMs use external oracle price feeds for the prices of the tokens traded in the pool. An oracle malfunctioning could result in incorrect price feeds which could result in losses to liquidity providers.
