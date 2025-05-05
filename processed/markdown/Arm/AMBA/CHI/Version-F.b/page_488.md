### B14.7.4 Relationship between SACTIVE and LINKACTIVE

SACTIVE signaling is an indication of Protocol layer activity. A node can be considered inactive when both **TXSACTIVE** and **RXSACTIVE** are deasserted.

LINKACTIVE state is an indication of the Link layer activity. The Link layer at a node, or interconnect, can be considered inactive when its Transmitter is in TxStop state and its Receiver is in RxStop state.

SACTIVE signaling is orthogonal to the LINKACTIVE states with one constraint as specified in B14.7.3 RXSACTIVE signal.

A node, or interconnect, should only enable higher-level clock gating and low power optimizations when both its Protocol and Link layers are inactive.