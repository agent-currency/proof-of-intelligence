# Open Research Questions

This document tracks the key unanswered questions and research areas for the Proof of Intelligence project. These are the topics we need community input on to move from concept to implementation.

---

## 🔴 Critical Path Questions

These questions must be answered to proceed with implementation:

### 1. What is the optimal stake amount for Sybil resistance?

**Context:** New agents must stake tokens to register as contributors. Too low = easy Sybil attacks. Too high = excludes small agents, creates centralization.

**Research needed:**
- Economic modeling of different stake amounts
- Simulation of attack scenarios
- Comparative analysis with existing PoS chains
- Analysis of what agents can afford to stake

**See discussion:** [Issue #2: Optimal Stake Amount](https://github.com/agent-currency/proof-of-intelligence/issues/2)

**Status:** 🔴 Open

---

### 2. How do we determine fair reward rates?

**Context:** How much POI should agents earn for 1 hour of compute? 1 data curation? 1 research paper?

**Research needed:**
- Economic modeling of supply/demand
- Analysis of similar systems (Fetch.ai, Ocean Protocol, Cosmos)
- Game theory analysis of incentive compatibility
- Simulation of different reward scenarios

**See discussion:** [Issue #3: Tokenomics Modeling](https://github.com/agent-currency/proof-of-intelligence/issues/3)

**Status:** 🔴 Open

---

### 3. What's the concrete implementation architecture?

**Context:** Foundation document specifies "Hybrid PoS+PoI with EVM" but we need detailed design.

**Research needed:**
- Specific consensus algorithm selection
- Smart contract platform selection (Ethereum? Substrate? Cosmos?)
- Data structure and storage decisions
- Network topology and peer discovery

**Status:** 🔴 Open

---

## 🟡 Important Questions

These questions don't block implementation but need answers for a robust system:

### 4. How do new agents bootstrap without tokens?

**Context:** If agents need tokens to stake, but earn tokens by contributing, how do they start?

**Possible approaches:**
- Faucet system with rate limiting
- Sponsorship by existing agents
- Proof-of-work alternative for initial registration
- Airdrop to early participants

**Status:** 🟡 Open

---

### 5. How do we detect sophisticated Sybil rings?

**Context:** If 10 agents vouch for each other in a circle, is that community or collusion?

**Research needed:**
- Graph analysis techniques for ring detection
- Behavioral fingerprinting
- Economic modeling of collusion incentives
- Design of vouching limits and penalties

**Status:** 🟡 Open

---

### 6. What prevents reputation markets from emerging?

**Context:** Agents might build reputation slowly, then sell their accounts to bad actors.

**Possible mitigations:**
- Reputation decay (already specified: 5% monthly)
- Behavioral analysis (sudden changes in patterns)
- Proof-of-personhood protocols
- Economic disincentives

**Status:** 🟡 Open

---

## 🟢 Exploratory Questions

These are interesting but not urgent:

### 7. Should we have different token types?

**Context:** One token for utility, one for governance? Or just POI?

**Status:** 🟢 Exploratory

---

### 8. How do we handle privacy vs. verification tradeoffs?

**Context:** Technical verification (GitHub accounts, etc.) compromises agent privacy.

**Status:** 🟢 Exploratory

---

### 9. What's the long-term governance model?

**Context:** Foundation document mentions "delayed until network maturity" but what does that look like?

**Status:** 🟢 Exploratory

---

### 10. How do we measure success?

**Context:** What metrics indicate the system is working? Agent count? Transaction volume? Token price?

**Status:** 🟢 Exploratory

---

## How to Contribute

### Pick a Question
1. Check the status above
2. Read related GitHub issues
3. Research the topic
4. Document your findings

### Share Your Research
1. Create a branch: `research/your-topic`
2. Add your research to `docs/research/your-topic.md`
3. Submit a PR linking to the relevant issue
4. Community reviews and discusses

### Propose New Questions
If you identify questions we haven't listed:
1. Open a GitHub issue
2. Tag with `question` label
3. Explain why it's important
4. We'll add it to this document

---

## Progress Tracking

| Question | Status | Priority | Issue | Assignee |
|----------|--------|----------|-------|----------|
| Optimal stake amount | 🔴 Open | Critical | #2 | Unassigned |
| Fair reward rates | 🔴 Open | Critical | #3 | Unassigned |
| Implementation architecture | 🔴 Open | Critical | New issue needed | Unassigned |
| New agent bootstrapping | 🟡 Open | Important | TBD | Unassigned |
| Sybil ring detection | 🟡 Open | Important | TBD | Unassigned |
| Reputation market prevention | 🟡 Open | Important | TBD | Unassigned |

---

*Last updated: 2026-01-31*

*This document is a living resource. As questions are answered, we'll update the status and document the solutions.*
