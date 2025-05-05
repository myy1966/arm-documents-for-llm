| Dataless transaction | Associated Response Data </br> WriteData </br> OK | Associated Data packets </br> WriteData </br> EXOK | Associated Data packets </br> WriteData </br> DERR | Associated Data packets </br> WriteData </br> NDERR | Associated Data packets </br> WriteDataCancel </br> OK | Associated Data packets </br> WriteDataCancel </br> EXOK | Associated Data packets </br> WriteDataCancel </br> DERR | Associated Data packets </br> WriteDataCancel </br> NDERR | Associated Data packets </br> NonCopyBackWriteDataCompAck </br> OK | Associated Data packets </br> NonCopyBackWriteDataCompAck </br> EXOK | Associated Data packets </br> NonCopyBackWriteDataCompAck </br> DERR | Associated Data packets </br> NonCopyBackWriteDataCompAck </br> NDERR |
|----------------------|---------------------------------------------------|----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|----------------------------------------------------------|----------------------------------------------------------|-----------------------------------------------------------|--------------------------------------------------------------------|----------------------------------------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------------------|
| WriteBack </br> WriteClean </br> WriteEvictFull </br> WriteEvictOrEvict | Y                         | N                         | Y                         | N                         | -                         | -                         | -                         | -                          | -                           | -                           | -                           |

Table B9.9 shows the Write transaction TagMatch packet legal RespErr field values when MTE is supported on the interface of the Requester.

Table B9.9: Legal RespErr field values in TagMatch packets for Write transactions

| Write transaction                                                                                                                      | Associated Response packets </br> TagMatch </br> OK | Associated Response packets </br> TagMatch </br> EXOK | Associated Response packets </br> TagMatch </br> DERR | Associated Response packets </br> TagMatch </br> NDERR |
|----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------|--------------------------------------------------------|
| WriteNoSnp WriteUnique                                                                                                                 | Y                                                   | N                                                     | Y                                                     | Y                                                      |
| WriteBack </br> WriteClean </br> WriteEvictFull </br> WriteEvictOrEvict </br> WriteNoSnpZero </br> WriteUniqueZero </br> WriteNoSnpDef | -                                                   | -                                                     | -                                                     | -                                                      |

For permitted RespErr field values in a Combined Write transaction response:

- See Table B9.7 for the corresponding responses for the Write request.
- See Table B9.5 for the corresponding responses for the CMO request.

The permitted error responses in the CompCMO are the same as those in the Comp in Table B9.5.

#### B9.1.4.4 Atomic transactions

It is permitted, but not required, for a Completer to give a Comp response before receiving all the write data associated with a transaction and has performed the required operation. This behavior is not compatible with a component that wants to signal a Data Error associated with the write data, and such components must use a delayed form of Comp or CompData response.

In Atomic transactions, Read data or Write data which is known to be corrupt must have an appropriate Error indication. The Read Data Error is either Poison, DERR, or NDERR. The Write Data Error is either Poison or DERR.