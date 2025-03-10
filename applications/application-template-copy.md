# OmniRamp

- **Team Name:** Permissionless HQ
- **Payment Details:**
  - **DOT**: For the **DOT** compensation, please provide a Polkadot address (e.g. 15oF4...).
  - **Payment**: In case of payment in **USDC**, please provide a Polkadot AssetHub address and the currency (e.g. 15oF4... (USDC)). In the case of **fiat** payment, please share your bank account privately with grants@web3.foundation via your contact email (see below) and list here the date and time of your email (e.g. Fiat 24.12.1971, 11:59). 
- **[Level](https://grants.web3.foundation/docs/Introduction/levels):** 3

## Project Overview :page_facing_up:

### Overview

OmniRamp redefines fiat-to-crypto transition through a secure, decentralized peer-to-peer (P2P) trading protocol. Combining on-chain governance, cross-chain interoperability and privacy-first infrastructure to create a non-custodial marketplace that eliminates reliance on centralized exchanges (CEXs), empowering users trade fiat and crypto assets directly.

Leveraging Polkadot, OmniRamp bolsters Web3 adoption, bridging traditional finance and decentralized ecosystems while prioritizing security, accessibility, and user sovereignty.

**Core Value Proposition**

*Decentralized P2P Marketplace*

  - Non-Custodial Trading.

  - Assets are secured via a multi-signature escrow pallet, removing third-party custody risks.

  - Initial support for DOT/USD transitions, with ongoing research for other pairs.

*Cross-Chain Liquidity Engine*

  - Polkadot Native: Leverages XCM for seamless asset transfers across parachains (e.g., DOT, ASTR, USDT(AssetHub)).

  - Future Multi-chain Integration: Utilizes trustless bridges (Hyperbridge, Snowfork) to enable multi-chain p2p transitions.

*Privacy-First Compliance*

  - Zero-KYC Model: On-chain reputation scoring replaces centralized identity checks, prioritizing user privacy.

  - Privacy preserving chat platform.

*Dispute Resolution Framework*

  - DAO Arbitration: Decentralized collective of staked arbitrators to resolve conflicts, with penalties for malicious rulings.

  - Auto-Refund Mechanisms: Funds returned automatically if disputes remain unresolved for 1 Era(24H on Polkadot and 6H on Kusama).

**Team Motivation**

The team envisions OmniRamp as a clear delineation between permissionless systems and blockchain cartel-like operations, such as centralized exchanges (CEXs)

*Personal Pain Point*

CEX hacks has underscored the urgent need for permissionless systems to become the default user onramp for crypto adoption. Centralized platforms, while convenient, remain vulnerable to security breaches, regulatory risks, and operational failures. This incident highlights the inherent risks of entrusting assets to intermediaries, reinforcing the necessity of decentralized alternatives that empower users with full control over their funds and access to financial services without reliance on centralized entities.

*Decentralized Systems Advocates and Implementors*

Our team brings a decade of combined experience in:

- Substrate Development: Core contributors to Polkadot parachains since 2021 and current Polkadot fellowship members.

- Interoperability: Background in building cross-chain protocols(i.e. [Hyperbridge](https://github.com/polytope-labs/hyperbridge/graphs/contributors)).

- Governance: Architected DAOs(i.e. [Secretary Program](https://github.com/polkadot-fellows/runtimes/pull/347) for the polkadot fellowship).


*What Excites us Technically*

- Trustless Interop Transitions: Enabling cross-chain escrow without wrapped assets or bridge risks. # Does polkadot has a unified address for all connected chains?

- Reputation Pallet: Building sybil-resistant scoring purely on-chain.

- LibP2P Integration: Decentralizing communication layer.


## Project Details

### Protocol Overview
OmniRamp’s protocol enables seamless, decentralized fiat-crypto transitions through a four-step process:

*Offer Creation*

- Token Selection: Merchants list supported pairs(e.g., DOT/USD, DOT/EUR).

- Pricing: Set exchange rates (e.g., 1 DOT = $7 USD) and choose fiat payment methods (bank transfer, PayPal e.t.c).

*User Engagement*

- Order Matching: User (buyers/sellers) filter offers by action (Buy/Sell), pairs, price, and merchant reputation (1–5 stars).

- Escrow Initialization: Accepted Offers are secured via OmniRamp’s multi-sig escrow pallet, ensuring merchant cannot withdraw once a user initiates a transaction.

*Settlement*

- Off-Chain Payment: Payer (User or merchant) sends fiat via recipient’s preferred method (e.g., wire transfer, bank transfer, PayPal).

- Proof Submission: Buyer uploads encrypted payment proof (e.g., transaction ID) using LibP2P’s Noise Protocol.

*Asset Release or Dispute*

- Auto-Release: User / Merchant confirms payment within 1Era → escrow releases crypto to User / Merchant.

- Dispute Trigger: If unresolved, escrow locks funds and initiates DAO arbitration (7Era response window).


#### Escrow Model: Secure, Time-Bound Custody

OmniRamp’s escrow system ensures fairness and eliminates counterparty risk:

*Multi-Chain Escrow Pallets*

- Built on Substrate, escrow pallet initially support assets from Polkadot parachains (via XCM) with support for external chains (via bridges) in the near future.

- Funds are held in 2-of-3 multi-sig accounts, requiring buyer/seller/arbitrator consensus for release.

*Arbitration Mechanism*

- DAO Governance: Staked $RAMP holders vote on disputes, with votes weighted by stake size.

- Slashing: Arbitrators acting maliciously lose 50% of their stake.

- Auto-Refund: If seller doesn’t confirm/reject payment within 1Era, a dispute case is issued.

*Fraud Prevention*

1. Reputation Penalties

    - **Tiered Penalties**

        - First offense (unresponsiveness*): 10% reputation loss.

        - Repeat offenses: Penalty increases by 5% per incident (e.g., 15% on second offense).

        - After 3 offenses: Temporary suspension and mandatory resolution training.

    - **Appeal Process**: Allow sellers to contest penalties with evidence (e.g., technical issues, emergencies).

    - **Recovery Path**: Regain lost reputation through successful transactions (e.g., +5% per 5 completed orders).

2. Sybil Resistance

    - **Gradual Trust Building**: New Users: Start with low trade limits (e.g., $100 limit) until reputation is establised.

    - **Reputation Tiers**: limits change based on

        - Transaction history (e.g., 10+ successful trades unlocks $1,000 limit).

        - Community endorsements (e.g., reviews from trusted users).

        - Reputation penalties: Sellers lose 20% of their score for unresponsive behavior.

3. Malicious Behavior Detection

    - Contextual Reputation Deductions:

        - Minor failures (e.g., payment timeout): 5% reputation decrease.

        - Repeat failures (3+ in 7 days): 15% decrease + initiate abitrator review for intent.

        - Proven fraud: Account deletion.

    - Fraud Triggers:

        - Auto-flag users with high cancellation rates (>30%) or disputed orders.

        - Investigate patterns (e.g., users who only initiate only high-value trades).

4. Positive Reinforcement

    - Reward good actors with:

        - Reputation boosts for consistent on-time completions (e.g., +3% per 5 flawless trades).

        - Badges or perks (e.g., "Trusted Seller" status, reduced platform fees).

Benefits:

1. Funds remain on native chains via XCM, eliminating bridge risks while enabling multi-chain trading. Users retain custody without exposure to wrapped asset vulnerabilities.

2. 2-of-3 multi-sig escrow prevents unilateral fund access, while stake-weighted DAO arbitration aligns incentives for honest outcomes. Slashing disincentivizes malicious arbitrators.

3. Auto-refunds + reputation penalties create economic costs for bad actors. Sybil-resistant limits for new users reduce spam, while responsive sellers gain higher trade caps over time.


#### Cross-Chain Token Support (XCM)

*Unified Asset Availability*

- Merchants list tokens from supported chains (e.g., DOT from Relay Chain).

- Buyers purchase assets natively without wrapping (e.g., trade DOT for USDT on AssetHub directly via XCM).


*XCM Workflow*

(Lock-and-Transfer)When a buyer selects a cross-chain asset (e.g., USDT on AssetHub), OmniRamp:

- Locks USDT via escrow pallet's unified address on the source chain.

- Post-trade, unlocking the original asset and send to reciepient on the source chain.


Benefits:

1. No Bridge Risk: Avoids centralized bridging solutions prone to exploits.

2. Atomic Swaps: XCM ensures trades either complete fully or revert, eliminating partial failures.


**API Specifications:**

### 1. Order Matching Pallet

#### Functions
```rust
/// Create new P2P offer
#[pallet::weight(T::WeightInfo::create_order())]
#[pallet::call_index(0)]
pub fn create_order() -> DispatchResult;

/// Match existing order
#[pallet::weight(T::WeightInfo::match_order())]
#[pallet::call_index(1)]
pub fn match_order() -> DispatchResult;

/// Update order parameters
#[pallet::weight(T::WeightInfo::update_order())]
#[pallet::call_index(2)]
pub fn update_order() -> DispatchResult;

/// Cancel unfilled order
#[pallet::weight(T::WeightInfo::cancel_order())]
#[pallet::call_index(3)]
pub fn cancel_order() -> DispatchResult;

```

#### Data Structure
```rust
struct Order<AccountId, Balance> {
    creator: AccountId,
    pair: (AssetId, FiatCurrency),
    action: OrderAction,
    price: FixedU128,
    payment_method: PaymentMethod,
    quantity: Balance,
    status: OrderStatus, // Open/Matched/Cancelled
    created_at: BlockNumber,
}

enum OrderStatus {
    Open,
    Matched { counterparty: AccountId, matched_at: BlockNumber },
    Cancelled, // Cleanup cancelled orders from storage.
}
```

#### Events
```rust
OrderCreated(AccountId, OrderId, AssetId, FiatCurrency);
OrderMatched(OrderId, AccountId, AccountId); // order_id, maker, taker
OrderUpdated(OrderId, FixedU128, Balance);
OrderCancelled(AccountId, OrderId);
```

### 2. Escrow Pallet

#### Functions

```rust
/// Initiate Merchant into Escrow Pallet
/// The source chain of funds should add this escrow pallet as a proxy.
#[pallet::weight(T::WeightInfo::init())]
#[pallet::call_index(0)]
pub fn init() -> DispatchResult;


/// Lock funds for matched order
#[pallet::weight(T::WeightInfo::lock_funds())]
#[pallet::call_index(1)]
fn lock_funds() -> DispatchResult;

/// Release funds to counterparty
#[pallet::weight(T::WeightInfo::release_funds())]
#[pallet::call_index(2)]
fn release_funds() -> DispatchResult;

/// Initiate dispute resolution
#[pallet::weight(T::WeightInfo::initiate_dispute())]
#[pallet::call_index(3)]
fn initiate_dispute() -> DispatchResult;

```


#### Data Structures
```rust
struct Escrow<AccountId, Balance> {
    buyer: AccountId,
    seller: AccountId,
    asset: AssetId,
    amount: Balance,
    status: EscrowStatus,
    created_at: BlockNumber,
    timeout: BlockNumber,
}

enum EscrowStatus {
    Locked,
    Released(AccountId),
    Disputed(DisputeId),
    Refunded,
}

```

#### Events
```rust
FundsLocked(EscrowId, AccountId, Balance);
FundsReleased(EscrowId, AccountId);
DisputeInitiated(EscrowId, DisputeId);
AutoRefundTriggered(EscrowId);
```


#### 3. Reputation System Pallet

##### Functions
```rust
// Update reputation after trade completion
fn update_reputation() -> DispatchResult;

fn reputation_judgement() -> DispatchResult;
```


#### Events
```rust
ReputationUpdated(AccountId, u8);
PenaltyApplied(AccountId, u8); // Score reduction
```


##### 4. Governance & Dispute Pallet

#### Functions
```rust
/// Create new dispute case
fn create_dispute() -> DispatchResult;

/// Arbitrator vote on dispute
fn vote_on_dispute() -> DispatchResult;

/// Slash malicious arbitrator
fn slash_arbitrator() -> DispatchResult;

```

##### Data Structures
```rust
struct DisputeCase {
    escrow_id: EscrowId,
    claimant: AccountId,
    respondent: AccountId,
    status: DisputeStatus,
    votes: BTreeMap<AccountId, bool>,
    outcome: Option<bool>,
}

struct ArbitratorStake {
    account: AccountId,
    staked: Balance,
    successful_cases: u32,
    penalized: bool,
}
```

#### Data Structures
```rust
struct DisputeCase {
    escrow_id: EscrowId,
    claimant: AccountId,
    respondent: AccountId,
    status: DisputeStatus,
    votes: BTreeMap<AccountId, bool>,
    outcome: Option<bool>,
}

struct ArbitratorStake {
    account: AccountId,
    staked: Balance,
    successful_cases: u32,
    penalized: bool,
}

```

#### Events
```rust
DisputeCreated(DisputeId, EscrowId);
VoteRecorded(DisputeId, AccountId, bool);
DisputeResolved(DisputeId, bool);
ArbitratorSlashed(AccountId, Balance);

```

##### 6. XCM Integration

**Enabling cross-chain escrow and asset transfers via Polkadot’s native interoperability layer.**


**Technology Stack**
Blockchain Layer:

- polkadot-sdk

Communication

- LibbP2P

Storage

- IPFS


### Ecosystem Fit

Where does OmniRamp fit?
OmniRamp fills Polkadot’s critical gap in decentralized fiat access, serving as the missing bridge between traditional finance and multi-chain DeFi. Unlike CEX-centric solutions, it leverages:

Polkadot’s shared security.

XCM for cross-chain dispursment of assets.

##### Target Audience
End Users: Crypto newcomers needing low-friction fiat onboarding.

Parachains: Teams seeking fiat onramp liquidity bootstraping.

DEXs: Integrate fiat ramps via OmniRamp’s API (e.g., HydraDX).

##### Identified Needs
Problem: Developing markets lack access to CEXs (Chainalysis 2023).

Solution: P2P model reduces regional barriers (World Bank Findex Report 2021).

##### Competitive Landscape
Polkadot Ecosystem: No direct competitors; existing bridges lack fiat pairs.

External Ecosystems: Bisq (Bitcoin-only), LocalCryptos (Ethereum-centric, custodial escrow).

## Team :busts_in_silhouette:

### Team members

- Jesse Chejieh
- Damilare Akinlose

### Contact

- **Contact Name:** Jesse Chejieh
- **Contact Email:** jesse.chejieh@gmail.com
- **Website:** [permissionless-hq](https://github.com/permissionless-hq)

### Team's experience

Permissionless HQ is a collective of core blockchain engineers and builders from both protocol an application backgrounds, utilizing trustless, censorship-resistant architectures to redefine the blockchain application layer.

Jesse Chejieh - [Polkadot Fellowship Memebr](https://github.com/polkadot-fellows/seeding/pull/25) **add more**

Damilare Akinlose - [Polkadot Fellowship Member](https://github.com/polkadot-fellows/seeding/pull/41) **add more**

### Previous Grant Application

[Solidity Trie Verifier Implementation](https://github.com/w3f/Grants-Program/pull/1486) by Polytope Labs

[Interoperable State Machine Protocol](https://github.com/w3f/Grants-Program/pull/1645) by Polytope Labs

### Team GitHub Profiles

- https://github.com/{your_organisation}/{project_1}
- https://github.com/{your_organisation}/{project_2}

Please also provide the GitHub accounts of all team members. If they contain no activity, references to projects hosted elsewhere or live are also fine.

- https://github.com/{team_member_1}
- https://github.com/{team_member_2}

### Team LinkedIn Profiles (if available)

- https://www.linkedin.com/{person_1}
- https://www.linkedin.com/{person_2}

## Development Roadmap :nut_and_bolt:

### Overview

- **Total Estimated Duration:** 4 Months
- **Full-Time Equivalent (FTE):**  6 FTE
- **Total Costs:** $95,000 USD
- **DOT %:** 50% (Percentage of Total Costs to be paid in vested DOT)

### Milestone 1 Example — Order Maching and Escrow System

- **Estimated duration:** 1 month
- **FTE:**  1,5
- **Costs:** $35,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | We will provide both inline documentation of the code and a basic tutorial that explains how a user can spin up the annotation interface and perform basic tasks. |
| **0c.** | Testing and Testing Guide | Comprehensive unit and integration tests covering core functionality with detailed guide on test execution. |
| **0d.** | Docker | Containerized test environment with multi-node network simulation capabilities. |
| 0e. | OmniRamp Specification | We will put together a technical specification detailing the OmniRamp Protocol. |
| 1a. | Order Matching Pallet | Implement core order matching functionality and On-chain storage lookup optimizations. |
| 1b. | Order Matching Pallet(Benchmarking) | Design benchmarks for extrinsic weights. |
| 2a. | Multi-Sig Escrow Pallet | Implement 2-of-3 escrow management pallet. |
| 2b. | Multi-sig Escrow Pallet(Benchmarking) | Design benchmarks for extrinsic weights. |
| 3. | RPC APIs | JSPN-RPC endpoints for order book interaction. |


### Milestone 2 — DAO Abitration and Reputation System

- **Estimated Duration:** 1 month
- **FTE:**  1,5
- **Costs:** $30,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | We will provide both **inline documentation** of the code and a README stating objectives of DAO arbitration process and reputation system used by OmniRamp. |
| **0c.** | Testing and Testing Guide | Comprehensive unit and integration tests covering core functionality with detailed guide on test execution. |
| **0d.** | Docker | We will provide a Dockerfile(s) that can be used to test functionalities delivered with this milestone. |
| 1. | Governance Pallet & Arbitrator System | Implement abitrator initialization and stake-weighted voting with slashing for malicious rulings. |
| 2. | Reputation Pallet | On-chain scoring system, tracking transaction success rates and dispute history. Tiered penalties, sybli-resistant limits and on-chain recovery paths. |
| 3. | Dispute Workflow | Comprehensive testing of dispute lifecycle (initiation → evidence submission → DAO voting), using IPFS for evidence upload and updates. |


### Milestone 3 — Communication Protocol

- **Estimated Duration:** 1 month
- **FTE:**  1,5
- **Costs:** $15,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | LibP2P chat protocol specifications. |
| **0c.** | Testing and Testing Guide | Message encryption/decryption test suite. |
| **0d.** | Docker | Networked nodes with encrypted chat capabilities. |
| 1. | LibP2P Module | End-to-end encrypted chat protocol. |
| 2. | Reputation Integration | Auto-flag users based on reputation scores. |


### Milestone 4 — XCMP (AssetHub)

- **Estimated Duration:** 1 month
- **FTE:**  1,5
- **Costs:** $10,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 |
| **0b.** | Documentation | XCM asset fulfilment guides. |
| **0c.** | Testing and Testing Guide | Cross-chain test cases (OmniRamp ↔ Relay Chain ↔ AssetHub). |
| **0d.** | Docker | Multi-chain test environment. |
| 0e. | Article | Technical write-up published on Medium/Substack detailing protocol architecture. |
| 1. | XCM Escrow Adapter | Lock/unlock assets across parachains via ReserveAssetDeposit. |
| 2. | AssetHub Integration | Support USDT transfers on Polkadot AssetHub. |
| 3. | Unified Address System | Single account interaction across connected chains. |


## Future Plans

### Multichain Prolifiration
**Objective**: Expand OmniRamp as a multichain P2P platform enabled by verifiable interopreability powered by Hyperbridge.

## Additional Information :heavy_plus_sign:

**How did you hear about the Grants Program?** Web3 Foundation Website.
