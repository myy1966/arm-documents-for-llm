### B2.6.5 Transaction ordering

In addition to using a Comp response to order a sequence of requests from a Requester, this specification also defines mechanisms for ordering of requests between a Request Node, Home Node pair and an HN-I, SN-I pair. Between an HN-F, SN-F pair and HN-I, SN-I pair, the order field is used to obtain a Request Accepted acknowledgment.

Requester Order between an RN, HN pair and an HN-I, SN-I pair is supported by the Order field in a request. The Order field indicates that the transaction requires one of the following forms of ordering:

**Request Order**

This guarantees the order of multiple transactions, from the same agent, to the same address location.

**Endpoint Order**

This guarantees the order of multiple transactions, from the same agent, to the same endpoint address range.

**Ordered Write Observation, OWO**

This guarantees the observation order by other agents in the system, for a sequence of Write transactions from a single agent.

**Request Accepted**

This guarantees that the Completer sends a positive acknowledgment only when accepting the Read request.

Table B2.9 shows the Order field encodings.

Table B2.9: Order value encodings

| Order[1:0] | Description          | Permitted between              |
|------------|----------------------|--------------------------------|
| 0b00       | No ordering required | All                            |
| 0b01       | Request accepted     | HN-F to SN-F, and HN-I to SN-I |
|            | Reserved             | RN to HN                       |
| 0b10       | Request Order/OWO    | RN to HN ᵃ                     |
|            | Request Order        | HN-I to SN-I                   |
|            | Reserved             | HN-F to SN-F                   |
| 0b11       | Endpoint Order       | RN to HN, and HN-I to SN-I     |
|            | Reserved             | HN-F to SN-F                   |

- ᵃ Request Order when ExpCompAck = 0. OWO when ExpCompAck = 1.

#### B2.6.5.1 Ordering requirements

A Requester that changes the ordering requirements of a transaction to a stronger ordering requirement, is required to be consistent in changing the ordering requirement of Request Order to Endpoint Order on all its transactions.

The Order field must only be set to a non-0 value for the following transactions:

- ReadNoSnp
- ReadNoSnpSep
- ReadOnce*
- WriteNoSnp
- WriteNoSnpDef
- WriteNoSnp*CMO