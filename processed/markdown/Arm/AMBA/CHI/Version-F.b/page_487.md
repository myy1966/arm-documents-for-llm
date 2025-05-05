**TXSACTIVE** must be asserted after receiving an initiating snoop or SnpDVMOp flit, and no later than when its first Response flit is sent. An RN-F or RN-D component must keep **TXSACTIVE** asserted until after the final completing flit is sent for all Snoop transactions. The lifetime of a PrefetchTgt is a single flit. From the perspective of **TXSACTIVE** for the PrefetchTgt, the initiating flit of the a PrefetchTgt transaction is also the completing flit and the transaction can be considered complete in the following cycle after the flit is sent.

For an RN-F or RN-D, the **TXSACTIVE** output is the logical OR of the requirements for the Request interface and the Snoop interface.

## B14.7.2.2 TXSACTIVE signaling from a Subordinate Node

A Subordinate Node cannot initiate new transactions and is only required to assert **TXSACTIVE** while a transaction that is in progress is being processed.

A Subordinate Node must assert **TXSACTIVE** after receiving a transaction initiating flit and **TXSACTIVE** must be asserted before or in the same cycle in which its first Response flit is sent. The Subordinate Node must keep **TXSACTIVE** asserted until after the final completing flit is sent or received.

#### B14.7.2.3 TXSACTIVE signaling from an interconnect interface to a Request Node

The interconnect interface to a Request Node must assert **TXSACTIVE** in both the following conditions:

- On receiving a transaction initiating flit, a Request Node must be asserted before or in the same cycle in which its first Response flit is sent. The Request Node must keep **TXSACTIVE** asserted until after the final completing flit is sent or received.
- Before or in the same cycle in which its initiating Snoop or SnpDVMOp flit is sent. A Request Node must keep **TXSACTIVE** asserted until after the final completing flit is sent, which is either SnpResp or SnpRespData.

#### B14.7.2.4 TXSACTIVE signaling from an interconnect interface to a Subordinate Node

The interconnect interface to a Subordinate Node must assert **TXSACTIVE** before or in the same cycle in which its initiating Request flit is sent. The Subordinate Node must keep **TXSACTIVE** asserted until after the final completing flit is sent or received.

### B14.7.3 RXSACTIVE signal

When **RXSACTIVE** is asserted, the receiver must respond to a link activation request in a timely manner. It is permitted for a Receiver to delay responding to a Link activation request when **RXSACTIVE** is deasserted.

> **_NOTE:_** The deassertion of **RXSACTIVE** does not indicate that all Protocol layer activity has completed. A Receiver can receive a Protocol flit, which corresponds to a transaction that was in progress while **RXSACTIVE** was asserted, after **RXSACTIVE** is deasserted.

**RXSACTIVE** can be used in combination with a knowledge of the ongoing transactions, which is indicated by the components **TXSACTIVE** output, to indicate that no further transactions are required. This can be used to control entry to a low power state.