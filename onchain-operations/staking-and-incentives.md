---
canonical: https://docs.tally.xyz/tally-features/incentives-and-staking
description: Guide to token staking, incentive programs, and value accrual mechanisms
---

> Official documentation: [docs.tally.xyz/tally-features/incentives-and-staking](https://docs.tally.xyz/tally-features/incentives-and-staking)

# Staking and Incentives: A Complete Guide

Staking transforms passive token holders into active protocol participants. Done right, it aligns incentives, rewards contribution, and creates sustainable value accrual. Done poorly, it's just yield farming with extra steps.

This guide covers staking mechanics, incentive design, and how to build programs that reward the behavior you actually want.

---

## Why Staking Matters

Tokens without utility are just speculation. Staking gives tokens a job:

- **Value accrual:** Protocol revenue flows to stakers
- **Governance alignment:** Staked tokens participate in decisions
- **Security:** Staked tokens can secure networks or back insurance
- **Retention:** Lockups reduce sell pressure and reward long-term holders

The best staking programs tie rewards to actual contribution — not just locking tokens and waiting.

---

## Staking Mechanics

### Basic Staking

Users lock tokens in a contract and earn rewards over time:

- **Deposit:** Transfer tokens to staking contract
- **Accrue:** Rewards accumulate based on stake and time
- **Withdraw:** Unstake tokens (possibly with delay)
- **Claim:** Collect accrued rewards

Simple, but doesn't differentiate between passive holders and active participants.

### Staking with Governance

Staked tokens retain voting power:

- Users stake tokens and earn rewards
- Staked tokens can still delegate to governance representatives
- Rewards may depend on governance participation
- No tradeoff between yield and governance

This is critical. Traditional staking forces users to choose between earning rewards and participating in governance. Modern staking should support both.

### Liquid Staking

Users receive a liquid receipt token representing their stake:

- Deposit TOKEN, receive stTOKEN
- stTOKEN can be used in DeFi while earning staking rewards
- Unstaking burns stTOKEN and returns TOKEN
- Enables capital efficiency without sacrificing rewards

**Example:** Obol's stOBOL allows holders to earn staking rewards while maintaining liquidity and governance participation.

### Delegation-Based Staking

Rewards flow based on delegation, not just staking:

- Token holders stake and delegate to active participants
- Only tokens delegated to active governance participants earn rewards
- Creates demand for quality delegates
- Ties rewards directly to governance activity

**Example:** ZKsync's staking program requires delegation to delegates who voted in at least 2 of the last 5 proposals to earn rewards.

---

## Incentive Design Principles

### Reward What You Want

The fundamental question: what behavior are you trying to incentivize?

| Goal | Incentive Design |
|---|---|
| Long-term holding | Time-weighted rewards, lockup bonuses |
| Governance participation | Delegation requirements, voting rewards |
| Network security | Slashing for misbehavior, validation rewards |
| Liquidity provision | LP staking, protocol-owned liquidity |
| Active contribution | Reputation-based rewards, milestone bonuses |

### Avoid Mercenary Capital

DeFi 1.0 taught us what happens with pure yield farming:
- Capital flows to highest APY
- Farmers dump rewards immediately
- Protocol subsidizes selling pressure
- Yield drops, capital leaves

**Solutions:**
- Vest rewards over time
- Require governance participation for full rewards
- Use protocol-owned liquidity instead of emissions
- Implement veTokenomics (lock for voting power multipliers)

### Sustainable Economics

Rewards have to come from somewhere:

- **Protocol revenue:** Fees, spread, MEV redistribution
- **Inflation:** New token emissions (dilutes non-stakers)
- **Treasury:** Pre-allocated reward pools (finite)

The most sustainable programs distribute real protocol revenue rather than inflating supply.

---

## Advanced Staking Features

### Delegate Reputation Scores (DRS)

Measure and reward quality governance participation:

- **Scoring:** 0-100 based on voting participation, rationale quality, engagement
- **Eligibility:** Only delegates above threshold (e.g., 65+) qualify for rewards
- **Updates:** Scores recalculate after each governance cycle
- **Transparency:** Scores visible on delegate profiles

This ensures rewards flow to active, engaged participants — not just large token holders.

### Delegate Compensation

Pay delegates for their governance work:

- Separate reward pool for delegate compensation
- Distributed based on voting power and reputation
- Square root models reduce whale concentration
- Minimum reputation thresholds for eligibility

**Example:** Obol distributes 165,000 OBOL over six months to delegates with DRS ≥ 65, using square root of voting power to flatten reward distribution.

### Fee Distribution

Return protocol revenue to stakers:

- Protocol governance decides percentage to distribute
- Automated distribution through smart contracts
- Rewards in native tokens, ETH, stablecoins, or other assets
- Creates direct link between protocol usage and token value

### Network Validation

Staked tokens can secure actively validated services:

- Compatible with protocols like EigenLayer and Symbiotic
- Aligns token holder incentives with network security
- Slashing for misbehavior creates accountability
- Restaking enables capital efficiency across services

### Insurance Funds

Staked tokens can back protocol insurance:

- Cover losses from hacks, bugs, or reorgs
- Stakers earn premium for taking on risk
- Slashing if insurance is triggered
- Aligns staker incentives with protocol security

---

## Case Study: ZKsync's Staking Program

ZKsync uses Tally's staking infrastructure to create an economic feedback loop where governance participation drives rewards.

### Program Structure

- **Season 1:** 10M ZK rewards for 400M tokens staked
- **Season 2:** 25M ZK rewards for 1B tokens staked
- **APR:** Up to 10% for active participants

### How It Works

**Delegation-based rewards:**
Token holders must stake ZK and delegate to active participants. Active participants are delegates who voted in at least 2 of the last 5 governance proposals.

**Continuous reward streaming:**
Rewards distribute continuously over 30-day epochs, preventing yield discontinuities and giving stakers time to respond to changing conditions.

**Governance integration:**
Staked tokens retain full voting power. Eligibility criteria ties rewards to governance activity.

→ [Learn more](https://forum.zknation.io/t/tpp-12-zknomics-token-staking)

---

## Case Study: Obol's Delegate Compensation

Obol combines liquid staking with delegate compensation to reward quality governance contribution.

### Program Structure

- **Liquid staking:** stOBOL receipt token for staked OBOL
- **Delegate compensation:** 165,000 OBOL over 6 months
- **Eligibility:** DRS ≥ 65 required
- **Distribution:** Square root of voting power

### How It Works

**Reputation-gated rewards:**
Only delegates maintaining a Delegate Reputation Score of 65 or higher qualify for compensation. This ensures rewards flow to engaged participants.

**Flattened distribution:**
Square root model based on delegated voting power reduces centralization and better compensates smaller but engaged participants.

**Integrated experience:**
Delegates check eligibility, view accrued compensation, and claim rewards directly through Tally's interface.

→ [Read the case study](https://tally.mirror.xyz/6e3I6e4K2FL_dcv5cnDTnJdQ0NSpqFnENZBAs7zre4s)

---

## How Tally Handles Staking

[Tally](https://tally.xyz) provides integrated staking infrastructure that connects rewards to governance participation.

### What Tally Offers

**Governance integration:**
Unlike staking systems that force users to choose between yield and governance, Tally's solution supports both. Staked tokens retain voting power and can delegate to representatives.

→ [Documentation](https://docs.tally.xyz/tally-features/incentives-and-staking)

**Delegation-based rewards:**
Optionally require tokens to be delegated to active governance participants to earn rewards. Ties rewards directly to governance activity.

**Delegate Reputation Scores:**
Measure participation quality with scores from 0-100. Gate rewards to delegates meeting minimum thresholds.

→ [Documentation](https://docs.tally.xyz/tally-features/governance/delegate-reputation-score-drs)

**Delegate compensation:**
Reward active delegates for their governance work. Square root models reduce whale concentration.

→ [Documentation](https://docs.tally.xyz/tally-features/incentives-and-staking/delegate-compensation)

**Liquid staking support:**
Enable token holders to earn rewards while keeping tokens transferable and usable across DeFi.

**Fee distribution:**
Return protocol fees to stakers with automated smart contract distribution.

→ [Documentation](https://docs.tally.xyz/tally-features/incentives-and-staking/staking-customizations)

**Network validation:**
Compatible with staking and restaking protocols like EigenLayer and Symbiotic.

**Seamless user experience:**
Stake, track rewards, and manage positions through one intuitive interface.

### Integrated with the Full Lifecycle

Staking works alongside Tally's other infrastructure:

- **Token sales:** Launch with staking enabled from day one
- **Governance:** Staked tokens participate in voting and delegation
- **Airdrops:** Reward stakers with future distributions

### Proven at Scale

- [ZKsync](https://tally.xyz/gov/zksync) — 35M ZK distributed through staking program
- [Obol](https://tally.xyz/gov/obol) — Liquid staking + delegate compensation
- [Arbitrum](https://tally.xyz/gov/arbitrum), [Uniswap](https://tally.xyz/gov/uniswap), [Wormhole](https://tally.xyz/gov/wormhole) — Governance with staking integration

→ [Talk to Tally](https://tally.xyz/contact)

---

## Getting Started with Staking

### Design Questions

Before implementing staking, answer these:

1. **What behavior do you want to incentivize?** Holding? Governance? Security?
2. **Where do rewards come from?** Protocol revenue? Inflation? Treasury?
3. **Should staking integrate with governance?** (Usually yes)
4. **Do you need liquid staking?** DeFi composability vs. simplicity
5. **How will you prevent mercenary capital?** Lockups? Delegation requirements? Vesting?

### Implementation Steps

1. **Define program parameters:** Reward rates, lockup periods, eligibility criteria
2. **Deploy contracts:** Staking contract, reward distribution, liquid token (if applicable)
3. **Integrate with governance:** Ensure staked tokens can delegate and vote
4. **Launch gradually:** Start with limited rewards, expand based on participation
5. **Monitor and iterate:** Adjust parameters based on actual behavior

---

## Related Resources

- [Onchain Governance Guide](./onchain-governance-guide.md)
- [Token Sale Compliance Guide](../token-sales/token-sale-compliance.md)
- [History of Vesting](../token-sales/history-of-vesting.md)
- [Staking Documentation](https://docs.tally.xyz/tally-features/incentives-and-staking)
- [Staking Contracts](https://docs.tally.xyz/set-up-and-technical-documentation/staking-contracts)
- [Talk to Tally](https://tally.xyz/contact)
