## B4.2 Request types

Protocol requests are categorized as follows:

- For Read request transactions, a data response is provided to the Requester.
- For Dataless request transactions, no data response is provided to the Requester.
- For Write request transactions, data is moved from the Requester.
- For Combined Write request transactions, data is moved from the Requester and a cache maintenance operation is performed.
- For Atomic request transactions, data is moved from the Requester and a data response is provided to the Requester in some request types.
- For Stash request transactions, data can be moved within a system to improve performance.
- Other request transactions:

    - Do not involve any data movement in the system.
    - Can be used to assist with DVM maintenance.
    - Can be used to warm the memory controller for a following read request.

The following subsections enumerate the resulting transactions and their characteristics. See Chapter B12 Memory Tagging for a description of the Memory Tagging mechanism. See Table B12.3 for information on the permitted MTE TagOp values for each request. See Chapter C2 Communicating Nodes for information on Request communicating nodes.

> **_NOTE:_** It is legal for any transaction that is expected to target an HN-F, but not an HN-I, to target an HN-I. This can occur for an incorrect assignment of memory type for a transaction. It is required that the HN-I responds to such a transaction in a protocol-compliant manner.

### B4.2.1 Read transactions

Read transactions have the following common characteristics:

- Data must be included in the completion response to the Requester, except for MakeReadUnique request. For MakeReadUnique, a data response is optional.
- When Data response is provided, the transferred data can be from the Home Node, another Request Node, or a Subordinate Node.
- In Allocating Read transactions, received data, if cached, must be cached in a system coherent manner.
- In Non-allocating Read transactions, that is, ReadNoSnp and ReadOnce*, received data is not expected to be cached. If cached, data is not cached in a system coherent manner.
- The request can result in a cache state change at the Requester. See Table B4.4 for expected and permitted initial cache and Table B4.5 for final cache state at the Requester for each of the Read transactions.
- The request can result in a cache state change at other Request Nodes in the system. See Table B4.6 for expected and permitted cache states at the peer Request Nodes for each of the Read transactions.

See Chapter B6 Exclusive accesses for details on Exclusive attribute in read transactions.