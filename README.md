# CoinPrune - Deployable Block Pruning for Bitcoin

> :warning: **Warning:** This is experimental research code for personal investigation. _Do not use in production, you might lose Bitcoins!_ :warning:

Bitcoin was the first successful decentralized cryptocurrency and remains the most popular of its kind to this day.
Despite the benefits of its blockchain, Bitcoin still faces serious scalability issues, most importantly its ever-increasing blockchain size.
While alternative designs introduced schemes to periodically create snapshots and thereafter prune older blocks, already-deployed systems such as Bitcoin are often considered incapable of adapting corresponding approaches.

In our work, we revise this popular belief and present _CoinPrune_, a snapshot-based pruning scheme which is fully compatible to Bitcoin.
CoinPrune can be deployed through an opt-in velvet fork, i.e., without impeding the established Bitcoin network.
By requiring miners to publicly _announce_ and jointly _reaffirm_ recent snapshots on the blockchain, CoinPrune establishes trust into the snapshots' correctness even in the presence of powerful adversaries.
Our evaluation shows that CoinPrune reduces the storage requirements of Bitcoin already by two orders of magnitude today, with further relative savings as the blockchain grows.
In our experiments, nodes only have to fetch and process 5 GiB instead of 230 GiB of data when joining the network, reducing the synchronization time on powerful devices from currently 5 hours to 46 minutes, with even more savings for less powerful devices.

This repository contains the experimental research code used to implement CoinPrune based on Bitcoin Core v0.17.1.
All our adaptations to the original Bitcoin Core code are marked using the pre-processor directive `#ifdef COMSYS_COMPACTION` to ease browsability.

The required changes have been implemented by:
* Benedikt Kalde
* Arthur Drichel
* [Roman Matzutt](https://www.roman-matzutt.de)

### Snapshot Availability

In the near future, we plan to release the snapshots created for our evaluation and to continually update the snapshot repository.
Stay tuned.

### Publication

*  Roman Matzutt, Benedikt Kalde, Jan Pennekamp, Arthur Drichel, Martin Henze, Klaus Wehrle: How to Securely Prune Bitcoin's Blockchain. In 2020 IFIP Networking Conference (IFIP NETWORKING’20), IFIP, 2020.

### Acknowledgements

This work has been funded by the German Federal Ministry of Education and Research (BMBF) under funding reference numbers 16KIS0443, 16DHLQ013, and Z31 BMBF Digital Campus.
The funding under reference number Z31 BMBF Digital Campus has been provided by the German Academic Exchange Service (DAAD).
The responsibility for the content of this publication lies with the authors.

## Usage

> :warning: **Warning:** This is experimental research code for personal investigation. _Do not use in production, you might lose Bitcoins!_ :warning:

### Dependencies

```
sudo apt-get install pkg-config libboost-all-dev libssl-dev libevent-dev
```

### Compiling

```
make clean
./autogen.sh
./configure --disable-wallet --disable-tests --disable-bench
make
```
