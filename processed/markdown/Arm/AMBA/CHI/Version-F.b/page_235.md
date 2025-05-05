## B4.7 Cache state transitions at a Requester

This section specifies the cache state transitions and completion responses for the following request transactions:

- B4.7.1 Read request transactions
- B4.7.2 Dataless request transactions
- B4.7.3 Write request transactions
- B4.7.4 Atomic transactions
- B4.7.5 Other request transactions

### B4.7.1 Read request transactions

Table B4.37 shows the cache state transitions at the Requester, and the completion responses, for Read request transactions except for the MakeReadUnique transaction.

For details of the permitted completion responses and cache state transitions at the Requester for the MakeReadUnique transaction, both Non-exclusive and Exclusive, see B4.7.1.1 MakeReadUnique transaction.

The cache state in the Data response to the Requester from the Subordinate Node is UC, that is, CompData\_UC or DataSepResp\_UC irrespective of the original request type.

If Home sends DataSepResp in response to ReadNoSnp, ReadOnce, ReadOnceCleanInvalid, or ReadOnceMakeInvalid, it is expected to use DataSepResp\_UC.

The Requester must ignore the cache state in the CompData or DataSepResp response to ReadNoSnp, ReadOnce, ReadOnceCleanInvalid, and ReadOnceMakeInvalid and implicitly assume the cache state value to be I.

> **_NOTE:_** In a non-DMT data transfer, where the CompData response is sent from the Subordinate to Home, the cache state in the response can be either I or UC. It is expected that typically the design of a Subordinate can be simplified by always using UC. Home subsequently sends CompData to the Requester with the appropriate cache state value.

Table B4.37: Cache state transitions at the Requester for Read request transactions

| Request type         | Initial expected state | Initial permitted state | Final state | Comp responses                              | Separate responses            |
|----------------------|------------------------|-------------------------|-------------|---------------------------------------------|-------------------------------|
| ReadNoSnp            | I                      | -                       | I           | CompData\_UC, CompData\_I                   | RespSepData + DataSepResp\_UC |
| ReadOnce             | I                      | -                       | I           | CompData\_UC, CompData\_I                   | RespSepData + DataSepResp\_UC |
| ReadOnceCleanInvalid | I                      | -                       | I           | CompData\_UC, CompData\_I                   | RespSepData + DataSepResp\_UC |
| ReadOnceMakeInvalid  | I                      | -                       | I           | CompData\_UD\_PD, CompData\_UC, CompData\_I | RespSepData + DataSepResp\_UC |

Continued on next page