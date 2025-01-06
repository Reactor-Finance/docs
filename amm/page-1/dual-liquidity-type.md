---
description: >-
  Each Reactor LP can have its own type, depending on the expected price
  correlation level between the two tokens of the pair.
---

# Dual-liquidity type

## Volatile pairs <a href="#volatile-pairs" id="volatile-pairs"></a>

Volatile pairs are composed of uncorrelated assets, based on the usual UniV2 model, using the standard constant product formula:

$$
x∗y=k
$$

## Stable pairs <a href="#stable-pairs" id="stable-pairs"></a>

Stable pairs are used for correlated assets, and will try to maintain a 1:1 transfer ratio as much as possible. The formula is based on the well-known Solidly curve:

$$
x^3y+y^3x=k
$$
