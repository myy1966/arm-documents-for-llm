A DERR or NDERR can be signaled at the following points within a transaction:

- With the CompDBIDResp response.
- For an AtomicStore transaction, with the Comp response.
- For an AtomicLoad, AtomicSwap, and AtomicCompare transaction, with the CompData response.

> **_NOTE:_** If a read data at Home due to a non-store Atomic request results in a DERR or NDERR, such an error can be propagated onto the DBIDResp or CompDBIDResp response for that request.

For Atomic transactions that are not able to complete, a NDERR must be used. The transaction structure, including all write data transfers, read data transfers, and other responses must still take place.

There is no need to specify an error associated with the execution of an atomic operation, such as overflow. All atomic operations are fully specified for all input combinations.

A transaction includes both outbound and inbound data, but only has a single Error field. For Atomic transactions, it is permitted for the Error field to indicate an error on either write data or read data. There is no mechanism supported within the transaction to differentiate between the potential different causes of an error. A fault log, or a similar structure, could be able to provide such information, but this is not a requirement of the CHI protocol.

The permitted RespErr values in Atomic transactions are an amalgamation of those permitted in Read and Write transactions.

A DERR can vary between data packets.

Table B9.10 shows the Atomic transaction Response packets legal RespErr field values.

Table B9.10: Legal RespErr field values in Response packets for Atomic transactions

| Atomic transaction                              | Associated Response packets </br> DBIDResp | Associated Response packets </br> Comp </br> OK | Associated Response packets </br> Comp </br> EXOK | Associated Response packets </br> Comp </br> DERR | Associated Response packets </br> Comp </br> NDERR | Associated Response packets </br> CompDBIDResp </br> OK | Associated Response packets </br> CompDBIDResp </br> EXOK | Associated Response packets </br> CompDBIDResp </br> DERR | Associated Response packets </br> CompDBIDResp </br> NDERR |
|-------------------------------------------------|--------------------------------------------|-------------------------------------------------|---------------------------------------------------|---------------------------------------------------|----------------------------------------------------|---------------------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------------|------------------------------------------------------------|
| AtomicStore                                     | OK                                         | Y                                               | N                                                 | Y                                                 | Y Y                                                | Y                                                       | N                                                         | Y                                                         | Y                                                          |
| AtomicLoad </br> AtomicSwap </br> AtomicCompare | OK                                         | Y                                               | N                                                 | Y                                                 |                                                    | -                                                       | -                                                         | -                                                         | -                                                          |

Table B9.11 shows the Atomic transaction Data packets legal RespErr field values.

Table B9.11: Legal RespErr field values in Data packets for Atomic transactions

| Atomic transaction | Associated Response packets </br> WriteData </br> OK | Associated Response packets </br> WriteData </br> EXOK | Associated Response packets </br> WriteData </br> DERR | Associated Response packets </br> WriteData </br> NDERR | Associated Response packets </br> CompData </br> OK | Associated Response packets </br> CompData </br> EXOK | Associated Response packets </br> CompData </br> DERR | Associated Response packets </br> CompData </br> NDERR |
|--------------------|------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------|---------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------|--------------------------------------------------------|
| AtomicStore        | Y                                                    | N                                                      | Y                                                      | N                                                       | -                                                   | -                                                     | -                                                     | -                                                      |

Continued on next page