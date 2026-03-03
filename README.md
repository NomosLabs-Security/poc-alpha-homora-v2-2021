# Alpha Homora V2 Exploit PoC — Flash Loan Iron Bank Exploit

> **Educational Purpose Only** — This PoC is created for security research and education
> purposes only. It is a simplified simulation, not a fork replay against mainnet.

## Overview
- **Date:** 2021-02-13
- **Loss:** ~$37M
- **Chain:** Ethereum
- **Category:** Flash Loan Attacks
- **Block:** 11846647

## Vulnerability
Alpha Homora V2 allowed users to execute arbitrary "spell" contracts through HomoraBank. The attacker deployed a custom spell that performed repeated sUSD borrow/repay cycles through Iron Bank (Cream V2), exploiting a rounding error in the borrow share calculation to inflate borrowing capacity beyond actual collateral.

## Reproduction
```bash
git clone https://github.com/NomosLabs-Security/poc-alpha-homora-v2-2021
cd poc-alpha-homora-v2-2021
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Key Contracts
- `HomoraBank`: Core leveraged position manager (allowed arbitrary spell execution)
- `IronBank/Cream V2`: Lending market with borrow share rounding vulnerability
- `sUSD Market`: Low-liquidity market where rounding errors were amplified

## References
- [Alpha Finance Post-Mortem](https://blog.alphaventuredao.io/alpha-homora-v2-post-mortem/)
- [Cream Finance Statement](https://medium.com/cream-finance/c-r-e-a-m-finance-post-mortem-alpha-homora-v2-c3b3085c9571)

## License

MIT — For educational use only.
