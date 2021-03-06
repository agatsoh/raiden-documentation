---
description: >-
  Below you find a non-exhaustive list of known issues, which you should be
  aware of while using the current version of the software. Most of these issues
  are not Raiden specific, but rather apply to al
---

# Known Issues

* **Compromised user system:** If the system of the user is compromised and accessed by an attacker or if a malicious application is running, then the write-ahead logging \(WAL\) could be accessed and valuable information leaked through it, since the WAL is not yet encrypted as such: ****[**raiden-network/raiden\#579**](https://github.com/raiden-network/raiden/issues/579)
* **Disk Full:** The client does not properly handle the cases where the user's disk may be full. This could lead to a loss of data due to the Raiden node crashing. In the future, we want to handle the detection of a full disk and gracefully quit the app: ****[**raiden-network/raiden\#675**](https://github.com/raiden-network/raiden/issues/675)
* **Blockchain Congestion:** If the blockchain is congested and there is no space for the Raiden node to submit transactions on-chain, the client could end up being unable to settle the channel on-chain. The development of a gas slot based settlement timeout definition has been suggested in order to address blockchain congestion: [**raiden-network/raiden\#383**](https://github.com/raiden-network/raiden/issues/383)
* **Chain reorganizations:** The client used to have an issue with edge cases of chain reorganizations. These issues have been hot fixed by only polling events that are confirmed for 5 blocks. Same applies to processing transactions, which are assumed to be valid only after a confirmation period of 5 blocks. This results in 15 blocks wait time for opening a channel \(three on-chain transactions\).

