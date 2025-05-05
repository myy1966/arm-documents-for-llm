#### B4.2.1.2 Initial cache state at the Requester

Table B4.4 lists the permitted Requester cache states when a Request is sent. The following key is used for Table B4.4, Table B4.5 and Table B4.6:

- Y Yes, permitted
- Not permitted
- n/a Not applicable

Table B4.4: Permitted Requester cache state at the sending of Read request

| Request                     | Initial state   | Initial state   |    |    |    |     |     |
|-----------------------------|-----------------|-----------------|----|----|----|-----|-----|
|                             | UD              | UC              | SD | SC | I  | UDP | UCE |
| ReadNoSnp                   | -               | -               | -  | -  | Y  | -   | -   |
| ReadOnce                    | -               | -               | -  | -  | Y  | -   | -   |
| ReadOnceCleanInvalid        | -               | -               | -  | -  | Y  | -   | -   |
| ReadOnceMakeInvalid         | -               | -               | -  | -  | Y  | -   | -   |
| ReadClean TagOp = Transfer  | Y               | Y               | Y  | Y  | Y  | Y   | Y   |
| ReadClean TagOp != Transfer | -               | -               | -  | -  | Y  | -   | Y   |
| ReadNotSharedDirty          | -               | -               | -  | -  | Y  | -   | Y   |
| ReadShared                  | -               | -               | -  | -  | Y  | -   | Y   |
| ReadUnique                  | Y               | Y               | Y  | Y  | Y  | Y   | Y   |
| ReadPreferUnique            | -               | -               | Y  | Y  | Y  | -   | Y   |
| MakeReadUnique              | -               | -               | Y  | Y  | -  | -   | -   |

## B4.2.1.3 Final cache state at the Requester

Table B4.5 lists the permitted cache state at the Requester at the completion of the transaction.

Table B4.5: Permitted final Requester cache state

|                              | Final state   | Final state   |    |    |    |     |     |
|------------------------------|---------------|---------------|----|----|----|-----|-----|
| Request                      | UD            | UC            | SD | SC | I  | UDP | UCE |
| ReadNoSnp                    | -             | -             | -  | -  | Y  | -   | -   |
| ReadOnce                     | -             | -             | -  | -  | Y  | -   | -   |
| ReadOnceCleanInvalid         | -             | -             | -  | -  | Y  | -   | -   |
| ReadOnceMakeInvalid          | -             | -             | -  | -  | Y  | -   | -   |
| ReadClean TagOp = *Transfer* | Y             | Y             | Y  | Y  | -  | -   | -   |

Continued on next page