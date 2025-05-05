## B14.7 Protocol layer activity indication

This section describes the signals that indicate Protocol layer activity. It contains the following subsections:

- B14.7.1 Introduction
- B14.7.2 TXSACTIVE signal
- B14.7.3 RXSACTIVE signal
- B14.7.4 Relationship between SACTIVE and LINKACTIVE

### B14.7.1 Introduction

**SACTIVE** signaling indicates that there are transactions in progress.

**TXSACTIVE** is an output signal that is asserted by an interface where there is a transaction either in progress or about to start:

- **TXSACTIVE** must be asserted before or in the same cycle in which the first flit relating to a transaction is sent.
- **TXSACTIVE** must remain asserted until after the last flit relating to all transactions is sent or received.

This means that the deassertion of **TXSACTIVE** on an interface implies that the component has completed all transactions in progress and does not need to send or receive any further flits.

A transaction that is given a RetryAck response is considered to be in progress, **TXSACTIVE** must remain asserted until the associated credit has been supplied and used or returned.

**RXSACTIVE** is an input signal which indicates that the other side of the interface has ongoing Protocol layer activity. When **RXSACTIVE** is asserted a component must respond to Protocol layer activity in a timely manner.

**SACTIVE** signals must be synchronous to **CLK** and therefore are not required to be synchronized. If they cross a clock domain, the clock domain crossing bridge is required to synchronize the signals.

### B14.7.2 TXSACTIVE signal

The following rules apply to the **TXSACTIVE** signal:

- **TXSACTIVE** must be asserted when the transmitter has flits to send.
- A component that asserts **TXSACTIVE** must also, if required, initiate the link activation sequence. It is not permitted for a component to assert the **TXSACTIVE** signal and subsequently wait for the other side of the interface to initiate the link activation sequence.
- **TXSACTIVE** must remain asserted until after the last flit relating to all transactions is sent or received.
- It is permitted, but not required, for **TXSACTIVE** to be deasserted while transmitting link flits as part of the link deactivation sequence.

> **_NOTE:_** To ensure an efficient power down sequence, it is recommended not to assert a deasserted **TXSACTIVE** signal during a link deactivation sequence.

It is permitted for the interface on an interconnect component to use the RXSACTIVE input signal to directly generate the TXSACTIVE output signal. This behavior is only permitted on the interconnect interface and it is not permitted on any attached component.

Except for an interconnect interface of a Link, no other interface of a Link is permitted to loop-back the incoming **RXSACTIVE** onto the outgoing **TXSACTIVE**.