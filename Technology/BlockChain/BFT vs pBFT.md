# BFT(Byzantine Fault Tolerance) & p(practical)BFT

## Consensus

> A fundamental problem in   [distributed computing](https://en.wikipedia.org/wiki/Distributed_computing) and  [multi-agent systems](https://en.wikipedia.org/wiki/Multi-agent_system)  is to achieve overall system reliability in the presence of a number of faulty processes. This often requires processes to agree on some data value that is needed during computation.  

This process is called Consensus, which means the data identity of a decentralized network.

When there are many actors in the system who will not follow the rules and  do some evils in the system, how could the system tolerate the evils and stay healthy? Byzantine Fault Tolerance is a solution to these problems and will guarantee the construction of the consensus.

## The Two Generals Problem

Problem:
```
given:
	1. There are two generals leading two armies to attack a same enemy;
	2. One of the two generals is leader and the other is a follower;
  3. The enemy can only be defeated by the two armies together;
  4. To decide the time of attack, the leader general will send a messenger to tell the follwer the time of the attack;
  5. The messenger could be captured by the enemy and the message will not be delivered.
```

How can we guarantee the two armies achieving the same attack time as an agreement? Simply, just like a TCP connection, the follower can use an acknowledge message to inform the leader. But the tricky problem comes again: how can the follower know that the leader has received his ack? Maybe another message is required from the leader… At last, there will be infinite acks.

> There is no way to guarantee the second requirement that each general be sure the other has agreed to the attack plan. Both generals will always be left wondering whether their last messenger got through.  

This Two Generals Problem has been proven **unsolvable**.

## The Byzantine Generals Problem

This problem is a generalized version of the two generals problem with a twist. The leader-follower paradigm is transformed to a commander-lieutenant paradigm.

In the Byzantine Generals Problem, the commander will send a message to n - 1 lieutenants and at last, all of them must accept the same result, in other word, achieve a consensus.

Problem:

```
given:
	1. There are several generals leading their own divided armies camping outiside of the enemy's camp;
	2. There may be some traitors among the generals, they try to prevent the loyal generals from achieving an agreement on the attacking time.
  3. All loyal generals are trying to decide on a time to attack the enemy;
	4. A strong majority of the army is required to attack the enemy;
```

How can they guarantee such results:
1. All loyal generals achieve the agreement on the same attacking time;
2. All loyal generals should not only reach an  agreement, but also a reasonable agreement;

## Byzantine Faulty Tolerance

> Leslie Lamport proved that if we have 2m+1 correctly working processors, a consensus(agreement on same state) can be reached if at most m processors are faulty which means that strictly more than two-thirds of the total number of processors should be honest.  

**Four types of byzantine failures:**

* Failure to return a result
* Respond with an incorrect result
* Respond with a deliberately misleading result
* Respond with a different result to different parts of the system

**BFT is a property of either a system or a consensus algorithm rather than an algorithm itself.**

## pBFT

**A replication algorithm designed to be Byzantine Fault Tolerant**

**Advantages of pBFT:**

* **Energy Efficiency**: Can be accomplished without complex mathematical computations(like POW).
* **Transaction Finality**: Do not require multiple confirmations of each node.
* **Low Reward Variance**: Not clear enough, the article says that every node takes part in responding to the clients’ requests, hence every node can be incentivized leading to low variance in rewarding.

The pBFT can be divided into 4 phases:

1. The client send the request to the primary node;
2. The primary node multicast the req to the secondary node(replicas);
3. The secondary node process the req and respond to the client;
4. The client will accept the result if there are m+1 same results(m is the maximum number of faulty nodes allowed);

The primary node will change each view.

The limitation of pBFT:
* Sybil attacks: The pBFT is susceptible to Sybil attacks. As the number of the nodes increases, it will be more difficult to carry out the Sybil attacks. However, the scalability is also a limitation of pBFT.
* Scaling: pBFT does not scale well because of the overhead of its communication with other nodes. O(n^k) when the n is the number of messages and the k is the number of nodes;
* Non-Permission-less: First PBFT chooses a leader in round-robin fashion, however, this requires nodes to agree on a “membership list” of nodes to select from.

**Platforms using pBFT variants:**
	* Zilliqa – pBFT in combination with [PoW](https://contribute.geeksforgeeks.org/proof-of-workpow-consensus/) consensus
	* Hyperledger Fabric – permissioned version of pBFT
	* Tendermint – pBFT + DPoS(Delegated Proof-of-Stake)



[1][Understanding Blockchain Fundamentals, Part 1: Byzantine Fault Tolerance](https://medium.com/loom-network/understanding-blockchain-fundamentals-part-1-byzantine-fault-tolerance-245f46fe8419)
[2][practical Byzantine Fault Tolerance(pBFT) - GeeksforGeeks](https://www.geeksforgeeks.org/practical-byzantine-fault-tolerancepbft/)