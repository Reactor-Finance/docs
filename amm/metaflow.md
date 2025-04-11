---
description: Uniswap V3 & V4 Integration
---

# Metaflow

Uniswap has set the standard for decentralized exchanges (DEXs) through continuous innovation in automated market maker (AMM) technology. Uniswap V3 introduced concentrated liquidity, while Uniswap V4 enhances flexibility and efficiency with hooks and a singleton contract model.

### **Why build Metaflow in-house?**

Concentrated liquidity pools (clAMM) have proven to be a highly effective design for delivering low slippage onchain swaps. Early on we understood that, combined with Reactor's liquidity engine, clAMM pools would have the potential to capture a growing share of volume on the Monad Chain.&#x20;

After careful consideration, we decided Reactor would be best served if we designed a personalized implementation of clAMM for several reasons:

* Buying an existing solution was too costly and contradicted our promise to token holders of sharing 100% of protocol rewards.
* We couldn't find an efficient, decentralized AMM implementation that suited our product needs.
* We believed we could create a concentrated liq

### **Designing user-friendly concentrated liquidity**

Reactor is designed to reward liquidity providers. With Uniswap v3 and v4, RCT emissions flow exclusively to the liquidity staked within the price range boundaries of the pool's active trading price. In the context of concentrated liquidity, this could create an even larger [competitive advantage for professional market makers using concentrated pools](https://arxiv.org/pdf/2111.09192.pdf).

To reduce the constant need for re-balancing a deposit to remain within the incentivized price range, we've redesigned the minimal price range boundaries (tick space) based on the liquidity factors.

We came up with the following generally available choices for the concentrated pool types:

* For stable token pools, use a price range boundary of 0.5% (tick space 50) for tokens like USDC and USDT
* For volatile token pools, use a price range boundary of 2% (tick space 200) for tokens like RCT and MON

In addition to these, two more options are available on demand:

* For highly correlated tokens like stable coins and liquid staked tokens, a price range boundary of 0.01% (tick space 1) is available
* For emerging tokens like Reactor, a price range boundary of 20% (tick space 2000) is available to reduce liquidity pool re-balance needs

Finally, the pool fee was also redesigned to be adjusted independently from the pool type. Fees can now reflect partner protocols’ needs and can be adjusted based on the market's volatility. To reduce operational overhead, we are working on a dynamic fee module that will adjust itself on demand.
