Table B4.12: Permitted Requester cache state at the completion of a Dataless request

Table B4.10 – Continued from previous page

| Request               | Peer state <br> UD | Peer state <br> UC | Peer state <br> SD | Peer state <br> SC | Peer state <br> I | Peer state <br> UDP | Peer state <br> UCE | Peer state <br> No Change |
|-----------------------|--------------------|--------------------|--------------------|--------------------|-------------------|---------------------|---------------------|---------------------------|
| CleanUnique           | -                  | -                  | -                  | -                  | Y                 | -                   | -                   | -                         |
| MakeUnique            | -                  | -                  | -                  | -                  | Y                 | -                   | -                   | -                         |
| CleanShared           | -                  | Y                  | -                  | Y                  | Y                 | -                   | -                   | -                         |
| CleanSharedPersist    | -                  | Y                  | -                  | Y                  | Y                 | -                   | -                   | -                         |
| CleanSharedPersistSep | -                  | Y                  | -                  | Y                  | Y                 | -                   | -                   | -                         |
| CleanInvalid          | -                  | -                  | -                  | -                  | Y                 | -                   | -                   | -                         |
| CleanInvalidPoPA      | -                  | -                  | -                  | -                  | Y                 | -                   | -                   | -                         |
| MakeInvalid           | -                  | -                  | -                  | -                  | Y                 | -                   | -                   | -                         |

The Peer Request Node cache state at the completion of Evict, StashOnceUnique, StashOnceSepUnique, StashOnceShared, StashOnceSepShared is not applicable.

### B4.2.3 Write transactions

Write transactions move data from a Requester to a Completer, this could be the next level cache, memory, or a peripheral. The data being transferred, depending on the transaction type, can be coherent or non-coherent. Each write transaction must assert appropriate BE bits with the data.

#### B4.2.3.1 Immediate transactions

Immediate transactions, also known as Non-CopyBack Write transactions, are a subclass of Write transactions. Immediate Write transactions transfer data from Request Nodes to Home Nodes without initially obtaining coherent ownership of the data. Immediate Write transactions are also used to transfer data from Home Nodes to Subordinate Nodes.

Each Immediate Write transaction must assert the appropriate BE bits with the data. Immediate Write transactions can require snooping of other agents in the system.

In Immediate Write requests, except WriteNoSnpZero and WriteUniqueZero, DWT flow between the Request Node and the Subordinate Node is permitted only when the original request from the Request Node does not use OWO.

DWT flow between a Request Node and a Subordinate Node in WriteNoSnpZero and WriteUniqueZero is never permitted.

**WriteNoSnpFull**

Write a full cache line of data from a Request Node to a Non-snoopable address region, or write for a full cache line of data to any address region from the Home to Subordinate. All BE bits must be asserted.

**WriteNoSnpPtl**

Write up to a cache line of data from a Request Node to a Non-snoopable address region, or write up to a cache line of data to any address region from the Home to Subordinate. BE bits must be asserted for the appropriate byte lanes, including none or all, within the specified data size and deasserted in the rest of the data transfer.