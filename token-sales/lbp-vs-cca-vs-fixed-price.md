# LBP vs CCA vs Fixed-Price: Choosing a Token Sale Mechanism

The mechanism you choose for your token sale shapes everything: who participates, how price is discovered, how demand is handled, and what happens post-sale.

This guide compares the three main approaches — Liquidity Bootstrapping Pools (LBPs), Continuous Clearing Auctions (CCAs), and Fixed-Price Sales — so you can choose the right one for your project.

---

## Quick Comparison

| | LBP | CCA | Fixed-Price |
|---|---|---|---|
| **Price discovery** | Market-driven (declining curve) | Market-driven (uniform clearing) | Predetermined |
| **Handles oversubscription** | Yes (price rises) | Yes (pro-rata at clearing price) | Requires allocation rules |
| **Bot/MEV resistance** | Moderate | High | Low |
| **Complexity for buyers** | Medium | Medium | Low |
| **Post-sale liquidity** | Built-in (Balancer) | Built-in (Uniswap v4) | Separate step |
| **Best for** | Broad distribution, fair price discovery | Transparent auctions, institutional confidence | High conviction on price, simple UX |

---

## Liquidity Bootstrapping Pools (LBPs)

### How It Works

An LBP is a two-token pool where weights shift over time. The pool starts heavily weighted toward your token (e.g., 99% TOKEN / 1% USDC), creating a high initial price. Over the sale period, weights shift toward balance (e.g., 65% TOKEN / 35% USDC), causing the price to decline unless buyers step in.

**Example:** A pool starts at 1/99 USDC/TOKEN ratio with a high implied price. As weights decay toward 65/35, the price drops. Buyers waiting for a fair price buy in, which temporarily pushes price up. The final price reflects what the market actually thinks the token is worth.

### Advantages

- **Discourages speculation.** High starting price means bots and whales can't scoop up supply at the beginning. Buyers are incentivized to wait for a price they believe is fair.
- **Fair price discovery.** The market determines the price, not the team. No guessing required.
- **Broad distribution.** The declining price curve allows participation at various price points.
- **Low starting capital.** Teams only need to contribute 10-20% of the pool in stablecoins, versus 50% for a standard AMM pool.
- **Immediate liquidity.** Once the LBP concludes, tokens are immediately tradeable.

### Tradeoffs

- **Timing still matters.** While less susceptible than fixed-price sales, LBPs still execute immediately at submission time, creating some MEV exposure.
- **Complexity.** Buyers need to understand weight decay and price curves.
- **Requires monitoring.** Teams should watch the sale and be prepared to adjust if needed.

### When to Use

- You want the market to determine price
- You want broad, retail-friendly distribution
- You have limited starting capital
- You're comfortable with some price volatility during the sale

→ [Learn more about LBPs](https://docs.tally.xyz/token-sales/liquidity-bootstrapping-pools)

---

## Continuous Clearing Auctions (CCAs)

### How It Works

A CCA is a fully on-chain auction where bidders place orders specifying a budget and maximum price. The protocol automatically spreads each bid across the auction period according to a release schedule. At each clearing interval, all active bids are aggregated and a single clearing price is set.

**Example:** Alice bids $50,000 with a max price of $0.30/token. The protocol spreads her bid across all remaining auction blocks. At each block, the protocol finds the price where supply equals demand. If clearing price is $0.12/token, Alice (and everyone else) pays $0.12.

### Advantages

- **Uniform clearing = fairness.** All successful bidders pay the same price. No advantage to sophisticated traders.
- **MEV resistant.** Bids are spread over time and immutable once submitted. No sniping, no front-running.
- **Early bidding incentive.** Earlier bids get exposure to more clearing periods, naturally rewarding early participation without artificial bonuses.
- **Transparent.** Price discovery happens on-chain in real time. Participants can monitor and adjust.
- **Seamless liquidity transition.** Auction proceeds automatically seed a Uniswap v4 pool at the clearing price.

### Tradeoffs

- **Newer mechanism.** Less familiar to retail participants than LBPs or fixed-price sales.
- **Requires education.** Bidders need to understand max price, bid spreading, and clearing mechanics.
- **Parameterization matters.** Poor configuration (e.g., releasing too few tokens in the final period) can create manipulation risk.

### When to Use

- You want the most manipulation-resistant price discovery
- You're targeting institutional or sophisticated participants who value transparency
- You want automatic Uniswap v4 liquidity seeding
- You're comfortable educating your community on auction mechanics

→ [Learn more about CCAs](https://docs.tally.xyz/token-sales/continuous-clearing-auction)

---

## Fixed-Price Sales

### How It Works

You set a price. Buyers pay that price. If demand exceeds supply, you need allocation rules to determine who gets tokens.

**Example:** 10M tokens at $0.20 each, targeting a $2M raise. If 1,000 people want to buy $10,000 each but you only have $2M of supply, you need to decide how to allocate.

### Advantages

- **Simplicity.** Everyone understands fixed-price sales. No curves, no clearing, no complexity.
- **Control.** You decide the price. Useful if you have high conviction on valuation.
- **Predictable raise.** If you sell out, you know exactly how much you raised.

### Tradeoffs

- **Overpricing risk.** If you set the price too high, the sale doesn't sell out — a public failure.
- **Underpricing risk.** If you set the price too low, you leave money on the table and need allocation rules that may feel unfair (first-come-first-served favors bots; lotteries feel random; allowlists feel exclusive).
- **MEV vulnerable.** Fixed-price sales with first-come-first-served allocation are extremely susceptible to bots and front-running.
- **No price discovery.** You're guessing at fair value rather than letting the market decide.

### Allocation Strategies

If demand exceeds supply, you need rules:

- **Pro-rata:** Everyone gets a percentage of what they requested
- **Lottery:** Random selection among eligible participants
- **Allowlist:** Pre-approved addresses only
- **Eligibility scoring:** Weight allocation by protocol usage, NFT holdings, social following, etc.
- **Per-wallet caps:** Limit how much any single address can buy

### When to Use

- You have high conviction on the right price
- You want the simplest possible UX for buyers
- You have a clear allocation strategy for handling oversubscription
- You're targeting a specific community you can allowlist

→ [Learn more about fixed-price sales](https://docs.tally.xyz/token-sales/fixed-price)

---

## Real-World Examples

### MegaETH (Auction)

MegaETH ran a 72-hour English auction on Echo's Sonar platform. Result: $1.4B in bids competing for a $50M raise (28x oversubscribed). Over 100,000 participants completed KYC. The auction format handled extreme demand gracefully through pro-rata allocation at clearing price.

### Plasma (Fixed + Deposit)

Plasma opened a deposit vault targeting $250M. It filled immediately. They doubled to $500M — also filled in minutes. Final result: 1,110 contributors, median deposit $35,000, top 10 wallets = 38% of raise. Concentrated but successful.

### Monad (Fixed via Exchange)

Monad partnered with Coinbase for a US-regulated fixed-price sale. 7.5% of tokens at $0.025, targeting $187M. Result: $269M raised from 85,820 participants — but with friction. Participants needed Coinbase accounts and faced geographic restrictions. Community feedback was mixed.

### Hyperwave (LBP)

Hyperwave used an LBP on Balancer via Tally. Result: ~$500k raised with a custom branded interface. Seamless UX, fair price discovery, immediate post-sale liquidity.

---

## Decision Framework

**Choose LBP if:**
- You want market-driven price discovery
- You're targeting retail participants
- You want immediate liquidity on Balancer
- You have limited starting capital

**Choose CCA if:**
- You want maximum fairness and manipulation resistance
- You're targeting institutional or sophisticated participants
- You want automatic Uniswap v4 integration
- You can invest in community education

**Choose Fixed-Price if:**
- You have high conviction on valuation
- You want the simplest buyer experience
- You have a clear allocation strategy
- You're okay with the risks of mispricing

---

## How Tally Helps

[Tally](https://tally.xyz) supports all three mechanisms — LBP, CCA, and fixed-price — with:

- Branded, white-labeled sale pages on your domain
- Built-in KYC/KYB/KYI compliance
- Geo-blocking and region-specific lockups
- Post-sale liquidity seeding on Uniswap or Balancer
- Real-time dashboards for monitoring
- Launch-day support

Proven with [Arbitrum](https://tally.xyz/gov/arbitrum), [ZKsync](https://tally.xyz/gov/zksync), [Uniswap](https://tally.xyz/gov/uniswap), [Wormhole](https://tally.xyz/gov/wormhole), and more.

→ [Talk to the Tally team](https://tally.xyz/contact)

---

## Related Resources

- [How to Launch a Token](./token-sale-guide.md)
- [Token Sale Compliance Guide](./token-sale-compliance.md)
- [Token Sale Documentation](https://docs.tally.xyz/token-sales)
- [CCA Whitepaper](https://docs.uniswap.org/contracts/liquidity-launchpad/Overview)
- [Balancer LBP Documentation](https://docs.balancer.fi/concepts/explore-available-balancer-pools/liquidity-bootstrapping-pool.html)
