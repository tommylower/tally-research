---
canonical: https://docs.tally.xyz/tally-features/governance
description: Guide to onchain governance platforms and Tally's governance infrastructure
---

> Official documentation: [docs.tally.xyz/tally-features/governance](https://docs.tally.xyz/tally-features/governance)

# Onchain Governance: A Complete Guide

Onchain governance enables token holders to make binding decisions about protocol upgrades, treasury management, and community direction — all executed transparently through smart contracts. No intermediaries, no ambiguity about whether decisions will be implemented.

This guide covers how onchain governance works, what features matter, and how to implement production-ready governance for your protocol.

---

## Why Onchain Governance Matters

Traditional organizations make decisions through boards, executives, and legal agreements. Crypto protocols can do something different: encode decision-making directly into smart contracts where token holders vote and approved proposals execute automatically.

**Benefits:**
- **Transparency:** Every vote is recorded onchain. Anyone can verify the outcome.
- **Binding execution:** Approved proposals execute automatically. No one can block implementation.
- **Global participation:** Token holders anywhere can participate without intermediaries.
- **Credible neutrality:** Rules apply equally to everyone, including the founding team.

**The tradeoff:** Onchain governance requires upfront design work and ongoing participation. It's not right for every project, but for protocols seeking genuine decentralization, it's essential infrastructure.

---

## Core Components of Onchain Governance

### Governor Contract

The Governor contract manages the proposal and voting process:
- Proposal creation and submission
- Voting period management
- Vote counting and quorum verification
- Proposal state transitions (pending → active → succeeded/defeated → executed)

Most protocols use OpenZeppelin's Governor implementation or a compatible variant.

### Timelock Contract

The Timelock enforces a delay between proposal passage and execution:
- Gives the community time to react to approved proposals
- Allows users to exit if they disagree with a decision
- Provides security buffer against malicious proposals

Typical timelock delays range from 24 hours to 7 days depending on the protocol's risk profile.

### Governance Token

The token that grants voting power:
- Usually implements ERC20Votes for efficient vote delegation and tracking
- Voting power can be based on token balance, staked tokens, or delegated tokens
- Some protocols use non-transferable tokens for governance-only participation

---

## Key Governance Features

### Voting and Proposal Management

**Proposal creation:** Who can create proposals? Common approaches:
- Token threshold (e.g., must hold 1% of supply to propose)
- Delegate threshold (e.g., must have 10,000 delegated votes)
- Whitelist (only approved addresses can propose)

**Voting options:** Simple for/against, or for/against/abstain. Some protocols support multiple-choice voting.

**Quorum requirements:** Minimum participation needed for a vote to be valid. Too high and nothing passes; too low and small groups can push through controversial changes.

**Execution:** Approved proposals can execute arbitrary onchain actions — token transfers, parameter changes, contract upgrades, etc.

### Delegation

Token holders can delegate voting power to representatives without transferring tokens:

- **Full delegation:** All voting power goes to one delegate
- **Partial delegation:** Split voting power across multiple delegates
- **Self-delegation:** Retain your own voting power (required to vote directly)

Delegation is essential for governance participation at scale. Most token holders won't vote on every proposal, but they can delegate to someone who will.

### Security Councils

For critical protocol decisions, many projects establish security councils — small groups with authority to act quickly in emergencies:

- Multisig-based authority for emergency actions
- Democratic elections for council membership
- Time-limited terms with regular re-election
- Scope limitations (emergency only, not routine governance)

**Example:** Arbitrum's Security Council can execute emergency upgrades, with members elected by token holders through Tally's election infrastructure.

### Optimistic Governance

Streamline routine decisions by assuming proposals pass unless explicitly vetoed:

- Proposals enter a review period
- If no veto threshold is reached, proposal executes automatically
- Vetoes require significant token holder opposition
- Faster execution for non-controversial changes

Best for routine operational decisions, not major protocol changes.

### Multichain Governance (MultiGov)

As protocols deploy across multiple chains, governance needs to follow:

- Token holders on any chain can participate in governance
- Votes aggregate across chains
- Execution can happen on the chain where it's needed
- No bridging required for participation

---

## Governance Parameters

Getting these right is critical. Too restrictive and governance stalls; too loose and bad proposals pass.

| Parameter | Description | Typical Range |
|---|---|---|
| **Proposal threshold** | Tokens needed to create proposal | 0.1% - 1% of supply |
| **Quorum** | Minimum votes for validity | 2% - 10% of supply |
| **Voting period** | Time for voting | 3 - 14 days |
| **Voting delay** | Time between proposal and voting | 1 - 3 days |
| **Timelock delay** | Time between passage and execution | 1 - 7 days |

---

## Common Governance Challenges

### Voter Apathy

Most token holders don't vote. Solutions:
- Delegation to active representatives
- Gasless voting to remove friction
- Delegate compensation to incentivize participation
- Clear communication about important votes

### Governance Attacks

Malicious proposals or vote manipulation. Mitigations:
- Timelocks for exit opportunity
- Security councils for emergency response
- Quorum requirements for legitimacy
- Proposal thresholds to filter spam

### Plutocracy Concerns

Large holders dominate decisions. Considerations:
- Quadratic voting (square root of token weight)
- Delegate diversity programs
- Conviction voting (time-weighted)
- Reputation-based voting power

---

## How Tally Handles Governance

[Tally](https://tally.xyz) provides production-ready governance infrastructure used by the largest protocols in crypto.

### What Tally Offers

**Voting and proposal management:**
- Secure, transparent voting mechanisms
- Collaborative proposal creation tools
- No-code fund transfers
- Automatic execution of approved proposals

→ [Documentation](https://docs.tally.xyz/tally-features/governance/features)

**Delegation:**
- Full and partial delegation support
- Delegate discovery and profiles
- Integration with staking and token launch
- Delegation analytics

**Security council elections:**
- Democratic elections for council membership
- Custom-built election infrastructure
- Highest standards of integrity
- Used by Arbitrum for Security Council elections

→ [Documentation](https://docs.tally.xyz/tally-features/governance/security-council-elections)

**Optimistic governance:**
- Faster execution for routine decisions
- Configurable veto thresholds
- Community oversight maintained

→ [Documentation](https://docs.tally.xyz/tally-features/governance/optimistic-governance)

**Multichain support (MultiGov):**
- Govern from any chain
- Support for Solana, Ethereum, and EVM L2s
- No bridging required for participation

→ [Documentation](https://docs.tally.xyz/tally-features/governance/multigov)

**Gasless voting and delegation:**
- Remove financial barriers to participation
- Organizations cover transaction costs
- Increase participation rates

→ [Documentation](https://docs.tally.xyz/tally-features/governance/features#gasless-voting-and-delegation-relay)

**Delegate Reputation Score (DRS):**
- Measure governance participation quality
- Scores from 0-100 based on voting, rationales, engagement
- Enable reputation-gated rewards

→ [Documentation](https://docs.tally.xyz/tally-features/governance/delegate-reputation-score-drs)

### Proven at Scale

Tally powers governance for the largest protocols in crypto:

- [Arbitrum](https://tally.xyz/gov/arbitrum) — Security Council elections, protocol upgrades
- [ZKsync](https://tally.xyz/gov/zksync) — Community funding, protocol governance
- [Uniswap](https://tally.xyz/gov/uniswap) — Protocol governance, treasury management
- [Wormhole](https://tally.xyz/gov/wormhole) — Cross-chain governance
- [ENS](https://tally.xyz/gov/ens) — Domain governance
- [Hyperlane](https://tally.xyz/gov/hyperlane) — Interoperability governance
- [Obol](https://tally.xyz/gov/obol) — Distributed validator governance

**$40B+** in assets under governance · **1M+** users served

### Launch with Governance

Tally deploys production-ready governance as part of token launches:

- Deploy Governor and Timelock contracts
- ERC20Votes token with delegation support
- Claim & delegate flow for immediate participation
- Expert guidance on parameter configuration

→ [Talk to Tally](https://tally.xyz/contact)

---

## Getting Started with Governance

### For New Protocols

1. **Define governance scope:** What decisions will token holders control?
2. **Set parameters:** Proposal thresholds, quorum, voting periods
3. **Deploy contracts:** Governor, Timelock, governance token
4. **Launch delegation:** Enable token holders to delegate before first vote
5. **First proposal:** Start with something meaningful but low-risk

### For Existing Protocols

1. **Audit current governance:** What's working? What's not?
2. **Identify gaps:** Missing features? Poor participation?
3. **Plan migration:** If switching providers, plan carefully
4. **Communicate changes:** Give community time to adapt

---

## Related Resources

- [Token Sale Compliance Guide](../token-sales/token-sale-compliance.md)
- [Staking and Incentives Guide](./staking-and-incentives.md)
- [Governance Documentation](https://docs.tally.xyz/tally-features/governance)
- [Intro to Governance](https://docs.tally.xyz/user-guides/intro-to-governance)
- [Talk to Tally](https://tally.xyz/contact)
