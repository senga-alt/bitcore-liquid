# BitCore Liquid

**Intelligent Bitcoin Staking Infrastructure on Stacks**

---

## 📌 Overview

**BitCore Liquid** is a next-generation Bitcoin staking protocol built on the **Stacks blockchain**. It transforms idle Bitcoin into productive yield-bearing assets through **automated yield strategies**, **multi-layered risk management**, and **institutional-grade security mechanisms**.

The protocol issues **SIP-010 compliant liquid staking tokens (`lcBTC`)**, ensuring full composability across the Stacks DeFi ecosystem. By inheriting Bitcoin’s security through Stacks’ consensus, BitCore Liquid enables Bitcoin holders to confidently participate in DeFi while retaining the ability to use their liquid staking tokens in other protocols.

---

## ✨ Key Features

* **Algorithmic Yield Optimization**
  Adaptive yield strategies that respond dynamically to market conditions.

* **Multi-Layered Risk Management**
  Built-in risk scoring and automated protection mechanisms for user safety.

* **Optional Insurance Coverage**
  Treasury-backed coverage to protect stakers against protocol-level risks.

* **SIP-010 Compliant Liquid Token (`lcBTC`)**
  Composable token standard, enabling use across the Stacks ecosystem.

* **Real-Time Rewards**
  Yield distributions based on block intervals with flexible claiming.

* **Enterprise-Grade Governance**
  Transparent operations with owner-controlled configuration.

* **Native Bitcoin Security**
  Protocol inherits Bitcoin’s finality via Stacks’ consensus.

---

## 🏗️ System Architecture

At a high level, BitCore Liquid is composed of:

1. **Core Staking Pool**

   * Accepts and manages user deposits.
   * Tracks balances, rewards, and insurance coverage.

2. **Yield Engine**

   * Algorithmically calculates yield based on block intervals.
   * Updates pool-level and user-level rewards.

3. **Risk & Insurance Layer**

   * Maintains dynamic risk scores per user.
   * Allocates optional insurance coverage from treasury.

4. **Liquid Token (`lcBTC`)**

   * SIP-010 compliant fungible token.
   * Represents user’s share of the staking pool.
   * Fully transferable and composable across DeFi.

---

## 📜 Contract Architecture

The smart contract is implemented in **Clarity** with the following components:

### Constants & Errors

* Predefined error codes (`err-owner-only`, `err-pool-inactive`, etc.)
* Minimum stake amount (`0.01 BTC` in satoshis).

### Data Variables

* **Protocol State:** `total-staked`, `total-yield`, `yield-rate`, `pool-active`, etc.
* **Token Metadata:** `token-name`, `token-symbol`, `token-uri`.

### Data Maps

* `staker-balances` → Tracks lcBTC balances.
* `staker-rewards` → Accumulated rewards for each staker.
* `yield-distribution-history` → Record of past yield distributions.
* `risk-scores` → User-specific risk scoring.
* `insurance-coverage` → Tracks coverage amounts if enabled.
* `allowances` → SIP-010 allowance model for delegated transfers.

### Core Functions

* **Initialization:** `initialize-pool`
* **Staking Operations:** `stake`, `unstake`
* **Rewards:** `distribute-yield`, `claim-rewards`
* **Transfers:** `transfer`, `set-token-uri`
* **Queries:** `get-staker-balance`, `get-risk-score`, `get-pool-stats`

---

## 🔄 Data Flow (High-Level)

1. **Staking:**

   * User stakes BTC (represented in protocol units).
   * Balance, total supply, and risk score are updated.
   * Optional insurance coverage is provisioned.

2. **Yield Distribution:**

   * Owner triggers `distribute-yield` at valid intervals.
   * Yield is calculated based on staked supply and elapsed blocks.
   * Protocol updates global yield state and history.

3. **Claiming Rewards:**

   * User calls `claim-rewards`.
   * Rewards are added to user balance as `lcBTC`.

4. **Unstaking:**

   * User requests unstake.
   * Pending rewards are claimed automatically.
   * Balance and coverage are updated, tokens are burned.

---

## ⚙️ Deployment & Initialization

1. Deploy contract to the Stacks blockchain.
2. Initialize pool with desired APY rate:

```clarity
(contract-call? .bitcore-liquid initialize-pool u500) ;; 5% APY
```

3. Pool is now active; users can begin staking.

---

## 🔍 Read-Only Queries

* `get-name` → Returns token name (`Liquid Core BTC`).
* `get-symbol` → Returns token symbol (`lcBTC`).
* `get-balance` → Returns user’s lcBTC balance.
* `get-total-supply` → Total supply of lcBTC.
* `get-pool-stats` → Returns protocol-wide stats.
* `get-risk-score` → Returns user-specific risk score.

---

## 🚀 Future Extensions

* Cross-protocol integration with additional DeFi primitives.
* On-chain governance for community-led parameter adjustments.
* Extended insurance pools with third-party underwriters.
* Dynamic APY models linked to real-world Bitcoin yields.

---

## 📄 License

MIT License. Open for contributions and extensions.
