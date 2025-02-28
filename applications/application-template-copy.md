# OmniRamp

> [!NOTE]
> This document will be part of the terms and conditions of your agreement and, therefore, needs to contain all the required information about the project. Don't remove any of the mandatory parts presented in bold letters or as headlines (except for the title)! Lines starting with a `>` (such as this one) should be removed. Please use markdown instead of HTML (e.g., `![](image.png)` instead of `<img>`).
>
> See the [Grants Program Process](https://grants.web3.foundation/docs/process) on how to submit a proposal.

- **Team Name:** Legal name of your team (e.g. JsonCorp)
- **Payment Details:**
  - **DOT**: For the **DOT** compensation, please provide a Polkadot address (e.g. 15oF4...).
  - **Payment**: In case of payment in **USDC**, please provide a Polkadot AssetHub address and the currency (e.g. 15oF4... (USDC)). In the case of **fiat** payment, please share your bank account privately with grants@web3.foundation via your contact email (see below) and list here the date and time of your email (e.g. Fiat 24.12.1971, 11:59). 
- **[Level](https://grants.web3.foundation/docs/Introduction/levels):** 1, 2 or 3

> [!IMPORTANT]
> *The combination of your GitHub account submitting the application and the payment address above will be your unique identifier during the program. Please keep them safe.*

## Project Overview :page_facing_up:

### Overview

OmniRamp redefines fiat-to-crypto transition through a secure, decentralized peer-to-peer (P2P) trading protocol. Combining on-chain governance, cross-chain interoperability and privacy-first infrastructure to create a non-custodial marketplace that eliminates reliance on centralized exchanges (CEXs), empowering users trade fiat and crypto assets directly.

Leveraging Polkadot, OmniRamp bolsters Web3 adoption, bridging traditional finance and decentralized ecosystems while prioritizing security, accessibility, and user sovereignty.

**Core Value Proposition**

*Decentralized P2P Marketplace*

  - Non-Custodial Trading.

  - Assets are secured via multi-signature escrow pallet, removing third-party custody risks.

  - Initial support for DOT/USD transitions, with ongoing research for other pairs.

*Cross-Chain Liquidity Engine*

  - Polkadot Native: Leverages XCM (Cross-Consensus Messaging) for seamless asset transfers across parachains (e.g., DOT, ASTR, USDT(AssetHub)).

  - Multi-chain Integration: Utilizes trustless bridges (Hyperbridge, Snowfork) to enable multi-chain p2p transitions.

*Privacy-First Compliance*

  - Zero-KYC Model: On-chain reputation scoring replaces centralized identity checks, prioritizing user privacy.

  - Privacy preserving chat platform for seller to buyer comunnications.

  - ZK-Proof Verification: Sellers cryptographically confirm fiat receipts without exposing sensitive data.

*Dispute Resolution Framework*

  - DAO Arbitration: Decentralized council of staked arbitrators resolves conflicts, with penalties for malicious rulings.

  - Auto-Refund Mechanisms: Funds returned automatically if disputes remain unresolved for 24h.

**Team Motivation**

The team envisions OmniRamp as a clear delineation between permissionless systems and blockchain cartel-like operations, such as centralized exchanges (CEXs)

*Personal Pain Point*

CEX hacks has underscored the urgent need for permissionless systems to become the default user onramp for crypto adoption. Centralized platforms, while convenient, remain vulnerable to security breaches, regulatory risks, and operational failures. This incident highlights the inherent risks of entrusting assets to intermediaries, reinforcing the necessity of decentralized alternatives that empower users with full control over their funds and access to financial services without reliance on centralized entities.

*Decentralized Systems Advocates and Implementors*

Our team brings decades of combined experience in:

- Substrate Development: Core contributors to Polkadot parachains since 2021 and current Polkadot fellowship members.

- Interoperability: Background in building cross-chain protocols(i.e. Hyperbridge).

- Governance: Architected DAOs(i.e. Secretary Program).


*What Excites us Technically*

- Trustless Interop Transitions: Enabling cross-chain escrow without wrapped assets or bridge risks.

- Reputation Pallet Innovation: Building sybil-resistant scoring purely on-chain.

- LibP2P Integration: Decentralizing communication layers often overlooked in DeFi.


## Project Details

### Protocol Overview
OmniRamp’s protocol enables seamless, decentralized fiat-crypto transactions through a four-step process:

#### How It Works

*Offer Creation*

- Token Selection: Merchants list supported pairs(e.g., DOT/USD, ETH/USD, USDT/USD).

- Pricing: Set exchange rates (e.g., 1 DOT = $7 USD) and choose fiat payment methods (bank transfer, PayPal, mobile money).


*User Engagement*

- Order Matching: Users filter offers by action (Buy/Sell), token, price, and merchant reputation (1–5 stars).

- Escrow Initialization: Accepted Offers are secured via OmniRamp’s multi-sig escrow pallet, ensuring merchant cannot withdraw once a user initiates a transaction.


*Settlement*

- Off-Chain Payment: Buyer sends fiat via the seller’s preferred method (e.g., wire transfer).

- Proof Submission: Buyer uploads encrypted payment proof (e.g., transaction ID) using LibP2P’s Noise Protocol.


*Asset Release or Dispute*

- Auto-Release: Seller confirms payment within 24h → escrow releases crypto to buyer.

- Dispute Trigger: If unresolved, escrow locks funds and initiates DAO arbitration (24h response window).


#### Escrow Model: Secure, Time-Bound Custody

OmniRamp’s escrow system ensures fairness and eliminates counterparty risk:

*Multi-Chain Escrow Pallets*

- Built on Substrate, escrow pallet support assets from Polkadot parachains (via XCM) and external chains (via bridges).

- Funds are held in 2-of-3 multi-sig accounts, requiring buyer/seller/arbitrator consensus for release.

*Arbitration Mechanism*

- DAO Governance: Staked $RAMP holders vote on disputes, with votes weighted by stake size.

- Slashing: Arbitrators acting maliciously lose 50% of their stake.

- Auto-Refund: If seller doesn’t confirm/reject payment within 24h, funds return to buyer automatically.

*Fraud Prevention*

- Reputation penalties: Sellers lose 20% of their score for unresponsive behavior.

- Sybil resistance: New users face lower trade limits until reputation is established.


#### Cross-Chain Token Support (XCM) - Multichain support with hyperbridge

*Unified Liquidity Pool*

- Merchants list tokens from supported chains (e.g., DOT from Relay Chain, USDT from AssetHub, ASTR from Astar).

- Buyers purchase assets natively without wrapping (e.g., trade DOT for ETH directly via XCM).


*XCM Workflow*

(Lock-and-Mint)When a buyer selects a cross-chain asset (e.g., ETH), OmniRamp:

- Locks ETH on the origin chain via Snowfork’s Ethereum bridge.

- Mints a XCM voucher on OmniRamp’s parachain for escrow.

(Burn-and-Unlock)Post-trade, vouchers are burned, unlocking the original asset.

Benefits Over Competitors:

No Bridge Risk: Avoids centralized bridging solutions prone to exploits.

Atomic Swaps: XCM ensures trades either complete fully or revert, eliminating partial failures.

**API Specifications:**

- Mockups/designs of any UI components
- Data models / API specifications of the core functionality
- An overview of the technology stack to be used
- Documentation of core components, protocols, architecture, etc. to be deployed
- PoC/MVP or other relevant prior work or research on the topic
- What your project is *not* or will *not* provide or implement
  - This is a place for you to manage expectations and clarify any limitations that might not be obvious


Things that shouldn’t be part of the application (see also our [FAQ](../docs/faq.md)):

- The (future) tokenomics of your project
- For non-infrastructure projects—deployment and hosting costs, maintenance or audits
- Business-oriented activities (marketing, business planning), events or outreach

### Ecosystem Fit

Help us locate your project in the Polkadot/Substrate/Kusama landscape and what problems it tries to solve by answering each of these questions:

- Where and how does your project fit into the ecosystem?
- Who is your target audience (parachain/dapp/wallet/UI developers, designers, your own user base, some dapp's userbase, yourself)?
- What need(s) does your project meet?
- How did you identify these needs? Please provide evidence in the form of (scientific) articles, forum discussions, case studies, or raw data.
- Are there any other projects similar to yours in the Substrate / Polkadot / Kusama ecosystem?
  - If so, how is your project different? Please identify and assess any projects addressing the same need and explain how your project is distinct. Feel free to include applicable research data, statistics, or metrics.
  - If not, please indicate why such a project might not have been possible, successful, or attempted. 
- Are there any projects similar to yours in related ecosystems? 

## Team :busts_in_silhouette:

> [!IMPORTANT]
> Please note that the data provided in this section is for administrative and informational purposes only. All beneficiaries of a grant must also be listed in the KYC/KYB process during the application phase. See our [FAQ](https://grants.web3.foundation/docs/faq#what-is-kyckyb-and-why-do-i-have-to-provide-this-data) for more info.

### Team members

- Name of team leader
- Names of team members

### Contact

- **Contact Name:** Full name of the contact person in your team
- **Contact Email:** Contact email (e.g. john@duo.com)
- **Website:** Your website

### Legal Structure

- **Registered Address:** Address of your registered legal entity, if available. Please keep it in a single line. (e.g. High Street 1, London LK1 234, UK)
- **Registered Legal Entity:** Name of your registered legal entity, if available. (e.g. Duo Ltd.)

### Team's experience

Please describe the team's relevant experience. If your project involves development work, we would appreciate it if you singled out a few interesting projects or contributions made by team members in the past.

If anyone on your team has applied for a grant at the Web3 Foundation previously, please list the name of the project and legal entity here.

### Team Code Repos

- https://github.com/{your_organisation}/{project_1}
- https://github.com/{your_organisation}/{project_2}

Please also provide the GitHub accounts of all team members. If they contain no activity, references to projects hosted elsewhere or live are also fine.

- https://github.com/{team_member_1}
- https://github.com/{team_member_2}

### Team LinkedIn Profiles (if available)

- https://www.linkedin.com/{person_1}
- https://www.linkedin.com/{person_2}


## Development Status :open_book:

If you've already started implementing your project or it is part of a larger repository, please provide a link and a description of the code here. In any case, please provide some documentation on the research and other work you have conducted before applying. This could be:

- links to improvement proposals or [RFPs](https://grants.web3.foundation/docs/rfps) (requests for proposal),
- academic publications relevant to the problem,
- links to your research diary, blog posts, articles, forum discussions or open GitHub issues,
- references to conversations you might have had related to this project with anyone from the Web3 Foundation,
- previous interface iterations, such as mock-ups and wireframes.

## Development Roadmap :nut_and_bolt:

This section should break the development roadmap down into milestones and deliverables. To assist you in defining it, we have created a document with examples for some grant categories [here](../docs/Support%20Docs/grant_guidelines_per_category.md). Since these will be part of the agreement, it helps to describe *the functionality we should expect in as much detail as possible*, plus how we can verify and test that functionality. Whenever milestones are delivered, we refer to this document to ensure that everything has been delivered as expected.

Below we provide an **example roadmap**. In the descriptions, it should be clear how your project is related to Substrate, Kusama or Polkadot. We *recommend* that teams structure their roadmap as 1 milestone ≈ 1 month.

> [!CAUTION]
> If any of your deliverables are based on somebody else's work, make sure you work and publish *under the terms of the license* of the respective project and that you **highlight this fact in your milestone documentation** and in the source code if applicable! **Projects that submit other people's work without proper attribution will be immediately terminated.**

### Overview

- **Total Estimated Duration:** Duration of the whole project (e.g. 2 months)
- **Full-Time Equivalent (FTE):**  Average number of full-time employees working on the project throughout its duration (see [Wikipedia](https://en.wikipedia.org/wiki/Full-time_equivalent), e.g. 2 FTE)
- **Total Costs:** Requested amount in USD for the whole project (e.g. 12,000 USD). Note that the acceptance criteria and additional benefits vary depending on the [level](../README.md#level_slider-levels) of funding requested.
- **DOT %:** Percentage of Total Costs to be paid in (vested) DOT (≥ 50%)

### Milestone 1 Example — Basic functionality

- **Estimated duration:** 1 month
- **FTE:**  1,5
- **Costs:** 8,000 USD

> [!NOTE]
> **The default deliverables 0a-0d below are mandatory for all milestones**, and deliverable 0e at least for the last one.

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| **0a.** | License | Apache 2.0 / GPLv3 / MIT / Unlicense. See the [delivery guidelines](https://grants.web3.foundation/docs/Support%20Docs/milestone-deliverables-guidelines#license) for details. |
| **0b.** | Documentation | We will provide both **inline documentation** of the code and a basic **tutorial** that explains how a user can (for example) spin up one of our Substrate nodes and send test transactions, which will show how the new functionality works. See the [delivery guidelines](https://grants.web3.foundation/docs/Support%20Docs/milestone-deliverables-guidelines#documentation) for details. |
| **0c.** | Testing and Testing Guide | Core functions will be fully covered by comprehensive unit tests to ensure functionality and robustness. In the guide, we will describe how to run these tests. See the [delivery guidelines](https://grants.web3.foundation/docs/Support%20Docs/milestone-deliverables-guidelines#testing-guide) for details. |
| **0d.** | Docker | We will provide a Dockerfile(s) that can be used to test all the functionality delivered with this milestone. |
| 0e. | Article | We will publish an **article**/workshop that explains [...] (what was done/achieved as part of the grant). (Content, language, and medium should reflect your target audience described above.) |
| 1. | Substrate module: X | We will create a Substrate module that will... (Please list the functionality that will be implemented for the first milestone. You can refer to details provided in previous sections.) |
| 2. | Substrate module: Y | The Y Substrate module will... |
| 3. | Substrate module: Z | The Z Substrate module will... |
| 4. | Substrate chain | Modules X, Y & Z of our custom chain will interact in such a way... (Please describe the deliverable here as detailed as possible) |
| 5. | Library: ABC | We will deliver a JS library that will implement the functionality described under "ABC Library" |
| 6. | Smart contracts: ... | We will deliver a set of ink! smart contracts that will...


### Milestone 2 Example — Additional features

- **Estimated Duration:** 1 month
- **FTE:**  1,5
- **Costs:** 8,000 USD

...


## Future Plans

Please include here

- how you intend to finance the project's long-term maintenance and development,
- how you intend to use, enhance, and promote your project in the short term, and
- the team's long-term plans and intentions in relation to it.

## Referral Program (optional) :moneybag:

You can find more information about the program [here](https://grants.web3.foundation/docs/referral-program).

- **Referrer:** Name of the Polkadot Ambassador or GitHub account of the Web3 Foundation grantee
- **Payment Address:** Polkadot/Kusama (USDC) payment address. Please also specify the currency. (e.g. 15oF4... (USDC))

## Additional Information :heavy_plus_sign:

**How did you hear about the Grants Program?** Web3 Foundation Website / Medium / Twitter / Element / Announcement by another team / personal recommendation / etc.

Here you can also add any additional information that you think is relevant to this application but isn't part of it already, such as:

- Work you have already done.
- If there are any other teams who have already contributed (financially) to the project.
- Previous grants you may have applied for.
