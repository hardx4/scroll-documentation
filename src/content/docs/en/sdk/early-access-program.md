---
section: sdk
date: Last Modified
title: "Early Access Program"
lang: "en"
permalink: "sdk/early-access-program"
excerpt: "Help us sculpt the Scroll SDK by trying it out and giving us early feedback!"
# whatsnext: { "Scroll Rollup Process": "/en/technology/chain/rollup" }
---

> Thank you for being an early-access collaborator interested in Scroll SDK _(working name)_. Whether you’re a prover partner, RaaS provider, or a project looking to deploy an L2 or dApp Chain, we’re eager to hear your feedback.

---

# Scroll SDK Introduction

Scroll SDK allows anyone to quickly deploy an instance of the Scroll zkEVM and its rollup architecture for deploying an L2 on Ethereum.

In the medium term, it will allow for robust customization of an L2, including customizing its DA layer, base/settlement layer, native gas token, bridge logic, and more. Our goal is to build a robust stack focused on sovereignty and adaptability, with simple upgradability and flexible proof generation, all without locking new chains into shared governance, common asset pools, or business-source licensing.

<aside>
💡 Need someone added to [the GitHub repo](https://github.com/scroll-tech/scroll-sdk)? Please reach out to the Scroll team on Slack or Telegram (and please tag `@dghelm` ).

</aside>

## Current Feature Set

- Fully functional local devnet or Sepolia testnet deployment of Scroll’s current zkEVM and protocol
- Configurable deployment using Docker, Kubernetes, and Helm
- Tools for interacting and exploring your chain, including Blockscout, our Rollup Explorer, and a white-label Bridge UI

## Planned Feature Set

- Additional DevOps quality of life improvements for generating config files
- Rollup or Validium Mode (Modular DA: 4844, callData, Alt-DA Layers)
- Base layer flexibility (Ethereum mainnet, Scroll, or any EVM-compatible environment)
- Custom Gas Token (any ERC20 from the base layer)
- Plug-and-play proof generation using various Proof Generation service providers allowing for failover and elastic capacity (see [Scroll Stack Prover Aggregation Testing](https://www.notion.so/Scroll-Stack-Prover-Aggregation-Testing-1fda726927bb4d7d8222909f25fe121d?pvs=21))
- Adaptable finality time (making tradeoffs between finality time and on-chain costs)
- Out-of-the-box, contract auto-deployments for various commonly used protocols

<aside>
⚠️ Scroll SDK shares the same risks, centralized components, and rollup maturity as Scroll chain. We’re building fast, but it’s worth being familiar with the [L2Beat assessment of Scroll](https://l2beat.com/scaling/projects/scroll#).

</aside>

## Troubleshooting / FAQ

### How long is finality on Scroll chain?

Finality depends on the parameterization of how often your chain wants to finalize to Ethereum. Roughly, a batch is created every minute (containing ~20 blocks or 200 txs), and takes about 50 minutes to finalize on L1.

Our next upgrade with increase the variability on block speed, but also increase how many batches will fit in a proof. We may decide to lengthen finality in order to reduce on-chain costs and lower transaction fees. _(At 556k gas to finalize, each finalize tx costs ~$9.80 as of June 3, 2024)._

If you want to explore more, check out [https://scroll.io/rollupscan](https://scroll.io/rollupscan)

### How does finality work without running a prover?

The Scroll SDK defaults to the behavior seen on Scroll Sepolia.

If proofs are not generated and accepted by the Coordinator, the Rollup Relayer with call a function on the L1 Bridge to finalize the state root without a proof. (This method is not part of the mainnet contracts.)

The default timeout for this finalization is 3600 seconds, to approximate mainnet finalization latency. To alter this behavior in Scroll SDK, set the following variables in `config.toml`:

```toml
TEST_ENV_MOCK_FINALIZE_ENABLED = true
TEST_ENV_MOCK_FINALIZE_TIMEOUT_SEC = 3600
```

# Request for Feedback

This document and repo have been shared with you because you’re a valued collaborator.

We’d love to hear any feedback on rough edges, blockers, minimal required features, developer experience improvements, and wild directional ideas. Also, we’re still exploring names, so if we welcome feedback on “Scroll SDK” 🙂

Feel free to send this to us through GitHub Issues, HackMD writeups, Telegram messages (DM `@dghelm` if you don’t have a better channel), or by filling out [this form](https://tally.so/r/3xQdNr).

[Scroll SDK Feedback](https://tally.so/r/3xQdNr)