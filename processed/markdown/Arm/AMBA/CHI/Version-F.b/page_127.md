## B2.6 Ordering

This section describes the mechanisms that the protocol includes to support system ordering requirements. It contains the following sections:

- B2.6.1 Multi-copy atomicity
- B2.6.2 Completion response and ordering
- B2.6.3 Completion acknowledgment
- B2.6.4 Ordering semantics of RespSepData and DataSepResp
- B2.6.5 Transaction ordering

For the meaning of the terms EWA, Device, and Cacheable, see B2.7.3 Memory Attributes.

### B2.6.1 Multi-copy atomicity

The memory model used in this specification requires multi-copy atomicity. All compliant components must ensure that all write requests are multi-copy atomic. A write is defined as multi-copy atomic if both of the following conditions are true:

- All writes to the same location are serialized, therefore observed in the same order by all Requesters. Some Requesters could not observe all of the writes.
- A read of a location does not return the value of a write until all Requesters observe that write.

In this specification, two addresses are considered to be the same with respect to coherence,observability, and hazarding if their cache line addresses and Physical Address Space (PAS) attributes are the same.

### B2.6.2 Completion response and ordering

Table B2.7 shows the various transaction responses and any ordering guarantees they provide with respect to later transactions, either from the same agent or from another agent.

Table B2.7: Completion response and ordering

| Transaction                                           | Location                | Response                | Outcome                                                                                                                                                                             |
|-------------------------------------------------------|-------------------------|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Read                                                  | Cacheable               | CompData or DataSepResp | The transaction is observable to a later transaction from any agent to the same location.                                                                                           |
| Read                                                  | Cacheable               | RespSepData             | No earlier transaction will send a snoop to this Requester. All later transactions send a snoop only if required after the Home receives the CompAck response for this transaction. |
| Read                                                  | Non-cacheable or Device | RespSepData or CompData | The transaction is observable to a later transaction from any agent to the same endpoint address range.                                                                             |
| Write or Atomic                                       | Cacheable               | Comp or CompData        | The transaction is observable to a later transaction from any agent to the same location.                                                                                           |
| Write or Atomic                                       | Non-cacheable or Device | Comp or CompData        | The transaction is observable to a later transaction from any agent to the same endpoint range.                                                                                     |
| Dataless except for StashOnceSep and CleanInvalidPoPA |                         | Comp                    | The transaction is observable to a later transaction from any agent to the same memory location.                                                                                    |

Continued on next page