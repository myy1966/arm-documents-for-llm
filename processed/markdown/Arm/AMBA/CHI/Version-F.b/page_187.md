|                          | Final state   | Final state   |    |    |    |     |     |
|--------------------------|---------------|---------------|----|----|----|-----|-----|
| Request                  | UD            | UC            | SD | SC | I  | UDP | UCE |
| ReadClean                | -             | Y             | -  | Y  | -  | -   | -   |
| TagOp != Transfer        |               |               |    |    |    |     |     |
| ReadNotSharedDirty       | Y             | Y             | -  | Y  | -  | -   | -   |
| ReadShared               | Y             | Y             | Y  | Y  | -  | -   | -   |
| ReadUnique               | Y             | Y             | -  | -  | -  | -   | -   |
| ReadPreferUnique         | Y             | Y             | Y  | Y  | -  | -   | -   |
| MakeReadUnique(non-Excl) | Y             | Y             | -  | -  | -  | -   | -   |
| MakeReadUnique(Excl)     | Y             | Y             | Y  | Y  | -  | -   | -   |

#### B4.2.1.4 Peer cache state

Table B4.6 lists the permitted cache state at the peer Request Nodes at the completion of the transaction.

In response to a request, the Home must send the appropriate Snoops to ensure cached lines at the peer caches are either an expected or permitted final state.

Table B4.6: Permitted peer cache state at the completion of a Read request

| Request              | Peer final state </br> UD | Peer final state </br> UC | Peer final state </br> SD | Peer final state </br> SC | Peer final state  </br> I | Peer final state   </br> UDP | Peer final state  </br> UCE | Peer final state   </br> No Change |
|----------------------|---------------------------|---------------------------|---------------------------|---------------------------|---------------------------|------------------------------|-----------------------------|------------------------------------|
| ReadNoSnp            | n/a                       | n/a                       | n/a                       | n/a                       | n/a                       | n/a                          | n/a                         | n/a                                |
| ReadOnce             | Y                         | Y                         | Y                         | Y                         | Y                         | Y                            | Y                           | Y                                  |
| ReadOnceCleanInvalid | Y                         | Y                         | Y                         | Y                         | Y                         | Y                            | Y                           | Y                                  |
| ReadOnceMakeInvalid  | Y                         | Y                         | Y                         | Y                         | Y                         | Y                            | Y                           | Y                                  |
| ReadClean            | -                         | -                         | Y                         | Y                         | Y                         | -                            | -                           | -                                  |
| ReadNotSharedDirty   | -                         | -                         | Y                         | Y                         | Y                         | -                            | -                           | -                                  |
| ReadShared           | -                         | -                         | Y                         | Y                         | Y                         | -                            | -                           | -                                  |
| ReadUnique           | -                         | -                         | -                         | -                         | Y                         | -                            | -                           | -                                  |
| ReadPreferUnique     | -                         | -                         | Y                         | Y                         | Y                         | -                            | -                           | -                                  |
| MakeReadUnique ᵃ     | -                         | -                         | -                         | -                         | Y                         | -                            | -                           | -                                  |

- ᵃ For MakeReadUnique(Excl), peer caches can not be required to change state.

### B4.2.2 Dataless transactions

Request Nodes use Dataless transactions to perform coherent actions without the transfer of data from or to the Requester. The Dataless transactions, grouped for their common functionality, are: