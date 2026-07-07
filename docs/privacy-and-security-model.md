# Privacy and Security Model

XELIS Wallet's privacy properties come from two different places: things the wallet application does locally on-device, and things the underlying XELIS protocol does at the consensus level. It's worth separating the two, because they answer different threat models.

## What the wallet does locally

The wallet's job is to keep the private key safe and to make sure nothing sensitive ever leaves the device unencrypted:

- **Key generation happens on-device.** The keypair is created locally at wallet setup, not fetched from or registered with any server.
- **Keys are encrypted at rest.** The private key is stored on disk encrypted using a key derived from the user's password. Without that password, the file on disk isn't directly usable.
- **Signing happens locally.** When a transaction is created, it's fully constructed and signed on the user's device before anything is transmitted. The connected node only ever sees a completed, signed transaction ready to broadcast — it doesn't participate in signing and doesn't need the private key.
- **No telemetry.** The wallet doesn't phone home with usage data, and there's no analytics layer reporting on wallet activity.

This covers the "can someone who compromises the network, or the node I'm connected to, steal my funds" question — the answer is no, because the node never has anything it could use to sign a transaction on your behalf. What it doesn't cover is device-level compromise: if malware on the machine itself can read the decrypted key in memory, or if someone gets the password and the encrypted file, local encryption alone won't stop them. That's a limitation of any software wallet, not something specific to this one.

## What the protocol does: confidential transactions

Separately from wallet-level key handling, the XELIS blockchain itself is built so that transaction amounts and balances are private by default, using homomorphic encryption. A more detailed technical explanation of what homomorphic encryption is and how it applies here is at [homomorphic encryption in crypto](https://xeliswallet.com/learn/homomorphic-encryption-crypto/), but the practical summary is:

- **Transaction amounts are encrypted on-chain.** An outside observer looking at the public ledger can see that a transaction occurred, but not the amount transferred.
- **Balances are encrypted.** An account's balance, as stored on-chain, isn't readable by simply looking at the chain — only someone holding the corresponding private view key can decrypt it.
- **This is the default, not an opt-in mode.** There's no separate "private transaction" toggle to remember to use; every transaction works this way.

This is a different design from chains that support optional privacy features layered on top of an otherwise transparent ledger — on those, a user has to actively choose the private path each time, and in practice many don't. Making it the only path removes that choice, for better or worse depending on what a given user is optimizing for (some jurisdictions and use cases specifically want transaction transparency, which is a real trade-off worth being aware of, not just a point in favor of one design). A related concept — the zero-knowledge proofs used to make some of these guarantees provable without revealing the underlying data — is covered separately at [zero-knowledge proofs explained](https://xeliswallet.com/learn/zk-proofs-explained/).

## The seed phrase: the actual root of trust

Underneath both of the above sits the 25-word recovery phrase generated at wallet creation. It's worth being precise about what this actually is: it's not a password, and it's not a convenience feature. It's a human-readable encoding of the same cryptographic material as the private key itself. Anyone who has the words can reconstruct the wallet and move the funds, on any device, without needing the original password or the original machine.

That has two direct consequences that are easy to state but easy to underweight in practice:

1. There is no recovery path if the phrase is lost. No support request, password reset, or account verification process can restore access, because there's no central account in the first place.
2. The phrase deserves at least the same physical security as cash or a legal document — offline, physically stored, and not typed into anything connected to the internet outside of the wallet's own recovery flow.

A deeper explanation of seed phrases generally (not specific to this wallet) is at [seed phrase explained](https://xeliswallet.com/learn/seed-phrase-explained/), and the practical backup/recovery steps are covered in [getting started](getting-started.md) in this repo, and in the site's [security guide](https://xeliswallet.com/guides/security/).

## Why the source being open matters here

Because the wallet is open source, the actual implementation of key generation, encryption, and signing is available for independent review rather than being something users have to take on faith. That doesn't make the software immune to bugs, but it does mean the cryptographic claims made above are, in principle, independently verifiable rather than purely asserted.

## See also

- [What is XELIS Wallet?](what-is-xelis-wallet.md)
- [XELIS blockchain fundamentals](xelis-blockchain-fundamentals.md)
