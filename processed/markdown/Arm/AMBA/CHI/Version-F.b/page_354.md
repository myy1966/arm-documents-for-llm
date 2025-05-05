Table B9.1: Error response field encodings

| RespErr[1:0] | Name  | Description                                                                                                                                                                                                                           |
|--------------|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0b00         | OK    | Normal Okay. Indicates that either: </br> - The Normal access was successful. For WriteNoSnpDef, RespErr must be used in combination with Resp to establish the exact response. See Table B4.28. </br> - The Exclusive access failed. |
| 0b01         | EXOK  | Exclusive Okay. Indicates that either the read or write portion of an Exclusive access has been successful.                                                                                                                           |
| 0b10         | DERR  | Data Error                                                                                                                                                                                                                            |
| 0b11         | NDERR | Non-data Error                                                                                                                                                                                                                        |

A single transaction is not permitted to mix OK and EXOK responses.

A transaction with a Data response is required to include NDERR either in none or in all Data packets.

The mixing of OK and DERR responses within a single transaction is permitted.

The mixing of EXOK and DERR responses within a single transaction is permitted.

The mixing of OK and NDERR responses within a single transaction is permitted, which can occur only in transactions with both Data and Non-data responses.

The mixing of EXOK and NDERR is not permitted.

### B9.1.3 Errors and transaction structure

All transactions must complete in a protocol-compliant manner, even if they include an error response.

Error handling for a transaction that utilizes DMT is the same as the error handling for the same request without DMT.

Because there is no mechanism to propagate errors on requests or snoops, a request must not use DMT or DCT if an error is detected at the interconnect.

If the transaction contains data packets, the source of the data packets is required to send the correct number of packets, but the data values are not required to be valid.

The Resp field gives the cache states associated with a transaction and can be influenced by an error condition. See B4.5 Response types for more details on the legal Resp field values. In a response with a NDERR indication, the cache state encoded in Resp is permitted to be any value, including reserved values.

The Resp field in a response must have the same value for every packet of a Data message regardless of whether or not there is an error condition.

A Requester that receives a response with a NDERR for a Snoopable request must:

- For an Allocating transaction:

    - When the start state is I, the Requester must not allocate the received data.
    - If the request was sent from a Non-Invalid state, the Requester must leave the cached copy unchanged.

    In both cases, the cache state must not be changed.

    - The Allocating transactions are: