# XELIS Blockchain Fundamentals

XELIS Wallet is a client for the XELIS blockchain, and a fair amount of what makes the wallet's behavior sensible only makes sense with some context on the chain underneath it. This covers the three pieces most relevant to a wallet user: the BlockDAG structure, the mining algorithm, and where smart contracts fit into the roadmap.

## BlockDAG instead of a single chain

Most proof-of-work blockchains, Bitcoin included, are structured as a single linear sequence of blocks — each block has exactly one parent, and the chain grows one block at a time. XELIS instead uses a BlockDAG (directed acyclic graph of blocks), where multiple blocks can be produced and reference multiple parents rather than a single previous block.

The practical effect is that block production doesn't have to be strictly sequential the way it does on a linear chain — blocks that would otherwise be "orphaned" competitors on a linear chain can instead be incorporated into the DAG structure. Combined with a roughly 15-second block time, this is aimed at higher effective throughput and faster confirmation than a comparable linear-chain design would achieve at the same block time. This is a structural, protocol-level design choice — it doesn't change anything about how the wallet application itself is used day to day, but it's the reason block times and confirmation behavior look different from, say, Bitcoin or Monero.

## Mining: XELIS-HASH-V2

XELIS uses a proof-of-work algorithm called XELIS-HASH-V2, which is designed to be mineable on both CPUs and GPUs while resisting the kind of specialized ASIC hardware that dominates mining on chains like Bitcoin. The goal of that design choice is generally to keep mining accessible to a broader set of participants rather than concentrating it among a small number of large-scale ASIC operators — a similar motivation to why Monero periodically tweaks its own algorithm.

Whether CPU or GPU mining makes more sense for a given person depends on hardware already on hand and electricity costs, among other factors — a more detailed comparison of the two approaches is at [GPU vs CPU mining](https://xeliswallet.com/learn/gpu-vs-cpu-mining/). Mining isn't something the wallet application handles directly — it's a separate piece of software (a miner) that participates in block production and, if successful, receives block rewards to an address the wallet can then track and spend from. Practical mining setup details live on the site's [mining page](https://xeliswallet.com/mining/) rather than in the wallet documentation itself, since the wallet's role starts after coins already exist.

## Privacy at the protocol level

As covered in more detail in [privacy and security model](privacy-and-security-model.md), every XELIS transaction uses confidential amounts and encrypted balances by default, via homomorphic encryption rather than as an optional feature. This is a protocol-level property, not something the wallet adds on top — it holds regardless of which wallet client is used to interact with the chain.

## Smart contracts: on the roadmap, not yet live

Native smart-contract support is listed as part of the XELIS protocol roadmap rather than as a currently shipping feature. That distinction matters for anyone evaluating the chain against ones that already have programmable contracts in production — XELIS's current strengths are specifically around privacy-by-default and BlockDAG throughput, with programmability planned rather than available today. More detail on the direction being taken is at [XELIS smart contracts](https://xeliswallet.com/learn/xelis-smart-contracts/).

## Where XEL, the asset, fits into this

XEL is the native asset of the XELIS chain — it's what's mined, held, and transferred through the wallet. Questions specifically about supply, emission, and distribution are covered at [XELIS tokenomics](https://xeliswallet.com/learn/xelis-tokenomics/) rather than here, since that's a distinct topic from the consensus mechanics covered above. Current price information, where relevant, is tracked on the live [price page](https://xeliswallet.com/price/) rather than in static documentation, since that's the kind of figure that goes stale immediately in written form.

## Verifying chain activity independently

Because XELIS is a public blockchain, transactions and blocks can be inspected independently of any particular wallet, through a block explorer. This is a useful cross-check for confirming that a transaction actually made it onto the chain, separate from just trusting what the wallet's own interface reports. See the [explorer info page](https://xeliswallet.com/explorer/) for what's available there.

## See also

- [Privacy and security model](privacy-and-security-model.md)
- [What is XELIS Wallet?](what-is-xelis-wallet.md)
