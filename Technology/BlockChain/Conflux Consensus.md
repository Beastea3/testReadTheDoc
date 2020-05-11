# Conflux Consensus
#blockchain #reading

The performance of the standard Nakamoto consensus is bottlenecked by facts below:

1. Only one participant can be identified as the new contributor of the new block;
2. It will cost about tens of blocks to confirm a transaction, and this slowness is very essential for the consensus from attacking from malicious.

Bitcoin-NG improves the throughput but nothing for the slowness.

BFT(Byzantine fault tolerance) is a compromised way which compromises the decentralization of blockchains.

Main features of Conflux:
* Fast — confirming a transaction in only minutes
* Throughput — process thousands of transactions per minutes

DAG (direct acyclic graph)


**Throughput is not limited by the consensus any more but the processing capability of each node** 


Assumptions and guarantees of conflux:
* Honest nodes are synchronous, or with reasonable latency.
* Honest nodes have more power of block generation in total than malicious.
* Leave the incentive mechanism as future work.

## Experimental Results

20k full nodes deployed on 800 EC2s
Compared to two Nakamoto consensus approaches Bitcoin and GHOST.
Throughput: 11.62x Bitcoin and GHOST, 3.84x Algorand under 20Mbps bandwidth limit
5.76GB/h, about 6400  typical bitcoin transactions per second under 40Mbps.
4.5-7.4 seconds for confirmation under 20Mbps and 7.6-13.8 seconds under 40Mbps.

## Architecture
Conflux forms a DAG instead of a linear chain as traditional blockchains.
* Gossip Network: a modified implementation of Bitcoin Core.
* Pending Tx Pool: to store Transactions which have not been packed yet, and will be emptied after packed.
* Block Generator: besides PoW, Conflux can also work with any other mechanism that can maintain a stable block generation rate, such as proof-of-stake (PoS) .
* Local DAG State: to store all blocks.

## Consensus

**How to decide the pivot chain?**

> It computes the subtree sizes of each child in the parental tree and advances to the child block with the largest subtree, until it reaches a leaf block.   

**Ignore the post-appeared same transactions**

Conflux applies the GHOST rule to select its pivot chain.

## Additional Experimental results:
* Conflux has a higher block utilization than Bitcoin and GHOST, stay 99% in several scenarios. However, Bitcoin and GHOST decrease quickly with either the increase of block size or the decrease of generation interval.
* The Confirmation time of Conflux is similar to GHOST, and is much quicker than Bitcoin.
