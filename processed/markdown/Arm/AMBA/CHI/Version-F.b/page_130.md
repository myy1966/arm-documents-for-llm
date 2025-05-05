- A Request Node that wants to make use of DMT must include a CompAck response in ordered ReadNoSnp and ReadOnce* transactions.
- For Write transactions, CompAck can only be used for:

    - WriteUnique, WriteNoSnp, and their Combined Write variants, when they require OWO guarantees. See B2.6.5.3 Streaming Ordered Write transactions.
    - CopyBack write transactions where Home has provided a Comp response, indicating that the Requester must not send CBWrData. When Home provides a Comp response, a CompAck must be sent by the Requester regardless of the original ExpCompAck value. See B2.3.2.3 CopyBack Write.

For transactions between a Request Node and a Home Node, where the Home Node is the Completer, the Home Node must support the use of CompAck for all transactions that are required or permitted to use CompAck.

A Subordinate Node is not required to support the use of CompAck.

A Requester, such as an HN-F or HN-I that communicates with an SN-F or SN-I respectively, must not send a CompAck response.

Table B2.8 shows the Request types that require a CompAck response, and the corresponding Requester types that are required to provide that response. The following key is used:

- Y Yes, required
- N No, not required
- H Dependent on transaction flow chosen by - - Home in response to the CopyBack Write request
- O Optional
- \- Not applicable

Table B2.8: Requester CompAck requirement

| Request type        | CompAck required   | CompAck required   |
|---------------------|--------------------|--------------------|
|                     | RN-F               | RN-D, RN-I         |
| ReadNoSnp           | O                  | O                  |
| ReadOnce*           | O                  | O                  |
| ReadClean           | Y                  | -                  |
| ReadNotSharedDirty  | Y                  | -                  |
| ReadShared          | Y                  | -                  |
| ReadUnique          | Y                  | -                  |
| ReadPreferUnique    | Y                  | -                  |
| MakeReadUnique      | Y                  | -                  |
| CleanUnique         | Y                  | -                  |
| MakeUnique          | Y                  | -                  |
| CleanShared         | N                  | N                  |
| CleanSharedPersist* | N                  | N                  |
| CleanInvalid        | N                  | N                  |
| CleanInvalidPoPA    | N                  | N                  |

Continued on next page