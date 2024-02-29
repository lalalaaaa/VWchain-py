# Vwchain-A DECENTRALIZED SCALE-OUT BLOCKCHAIN LEDGER SYSTEM FOR WEB3.0

Our prototype experiment demonstrates that under typical daily bandwidth network conditions, EZchain's performance in all aspects approaches that of the accounts in centralized payment systems. This provides a solid infrastructure for realizing mobile payments in web3.0.

## arXiv: 

Here is the [arXiv link](https://arxiv.org/abs/2312.00281). Cite this work by:
```
@misc{xue2023scaleout,
    title={A Scale-out Decentralized Blockchain Ledger System for Web3.0},
    author={Lide Xue and Wei Yang and Wei Li},
    year={2023},
    eprint={2312.00281},
    archivePrefix={arXiv},
    primaryClass={cs.CR}
}
```

## Highlights

* Scalability: System throughput is directly proportional to node size, not constrained by bandwidth resources.
* Hardware Compatibility: Designed for consumer-grade hardware, supporting necessary storage, computation, and verification requirements.
* Efficient Transaction Confirmation: Strives to keep transaction confirmation delays within one minute.
* Decentralization and Security: Maintains strict adherence to decentralization principles and ensures robust security​​.

## Get started

This project provides two ways of initialization. The first method is designed to efficiently conduct experimental simulations, observe, and record various metrics of EZchain. All node scripts operate in a centralized manner to maximize the utilization of limited memory for simulating the operation of large-scale networks as much as possible. The second method closely resembles real distributed operation, where individual nodes run as processes with independent ports. Communication between nodes also utilizes UDP and TCP sockets. For convenience, we will refer to the first simulation as NON-DST (DST for distributed) and the second one as DST.

### Running simulation (NON-DST)

#### Environment setup

Python 3.8 or higher.

```
git clone https://github.com/lalalaaaa/VWchain-py.git

cd VWchain-py

pip install -r requirements.txt
```

#### Useful configuration options

These are some critical configuration options in the project, which can be modified in the `const.py` file.

* SAMPLE_NEIGHBORS_NUM controls the neighbors' number of each p2p node (include consensus and account).
* NODE_ACCOUNT_DELAY and ACC_ACC_DELAY control the delay of consensus node to account node and the delay of account node to account node (referring here to queuing delays, excluding transmission times).
* NODE_NUM controls number of consensus nodes in NON-DST mode.
* ACCOUNT_NUM controls number of account nodes in NON-DST mode.
* PICK_TXNS_NUM controls the upper limit of transactions packaged at one round (block), it should theoretically not exceed ACCOUNT_NUM^2/2.
* SIMULATE_ROUND controls the mining round.
* BANDWIDTH controls the network's bandwidth.
* HASH_DIFFICULTY controls the mining difficulty, i.e., the probability of successful mining in one hash computation.
* HASH_POWER controls the hash computing power, indicating the number of hashes computation performed per second.
* GENESIS_SENDER and GENESIS_MINER_ID represent genesis sender's address and genesis miner's ID.

#### Run

```
python3 Vwchain_simulate.py
```

or

```
./Vwchain_simulate.py
```

### Running simulation (DST, under development)

#### Environment setup

Python 3.8 or higher.

```
git clone https://github.com/lalalaaaa/VWchain-py.git

cd Vwchain

pip install -r requirements.txt
```

#### Useful configuration options

These are some critical configuration options in the project, which can be modified in the `const.py` file.

* DST_NODE_NUM controls number of consensus nodes in DST mode.
* DST_ACC_NUM controls number of account nodes in DST mode.
* MAX_PACKAGES signifies the threshold at which collective packaging into blocks occurs, when the transaction pool of consensus nodes reaches MAX_PACKAGES acctxns packages.
* ONE_HASH_TIME controls the time consumed by one hash calculation.
* ONE_HASH_SUCCESS_RATE controls the probability of a successful hash calculation, i.e., mining difficulty.
* The remaining parameters are as described in the NON-DST mode.

#### Run

```
python3 DST_ENTRY_POINT.py
```

or

```
./DST_ENTRY_POINT.py
```
