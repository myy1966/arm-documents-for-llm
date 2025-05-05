| Atomic transaction                              | Associated Response packets </br> WriteData </br> OK | Associated Response packets </br> WriteData </br> EXOK | Associated Response packets </br> WriteData </br> DERR | Associated Response packets </br> WriteData </br> NDERR | Associated Response packets </br> CompData </br> OK | Associated Response packets </br> CompData </br> EXOK | Associated Response packets </br> CompData </br> DERR | Associated Response packets </br> CompData </br> NDERR |
|-------------------------------------------------|------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------|---------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------|--------------------------------------------------------|
| AtomicLoad </br> AtomicSwap </br> AtomicCompare | Y                                                    | N                                                      | Y                                                      | N                                                       | Y                                                   | N                                                     | Y                                                     | Y                                                      |

Table B9.12 shows the Atomic transaction TagMatch packet legal RespErr field values when MTE is supported.

Table B9.12: Legal RespErr field values in TagMatch packets for Atomic transactions

| Atomic transaction                                                | Associated Response packets </br> TagMatch </br> OK | Associated Response packets </br> TagMatch </br> EXOK | Associated Response packets </br> TagMatch </br> DERR | Associated Response packets </br> TagMatch </br> NDERR |
|-------------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------|--------------------------------------------------------|
| AtomicStore </br> AtomicLoad </br> AtomicSwap </br> AtomicCompare | Y                                                   | N                                                     | Y                                                     | Y                                                      |

#### B9.1.4.5 Other transactions

This section describes the error handling requirements for the DVMOp and PrefetchTgt transactions.

##### B9.1.4.5.1 DVMOp

A DVMOp transaction can include a NDERR in the Comp response. The interconnect can consolidate error responses from all the snoop responses for a DVMOp and include a single error response in the final Comp message to the Requester. The DBIDResp packet must only use the OK response. Even though the Sender of a WriteData response might not use DERR, the packet can be marked as DERR if it encounters errors during transmission. See B9.2.3 Interoperability of Poison and DataCheck.

Table B9.13 shows the DVM transaction Response packets legal RespErr field values.