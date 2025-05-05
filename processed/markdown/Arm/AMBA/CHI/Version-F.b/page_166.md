- TraceTag
- RSVDC
- CAH

When the Requester receives a RetryAck response for a CopyBack Write request whose data is invalidated by a snoop, the Requester can either:

- Drop the Write request and return the received credit.
- Send the Write request with AllowRetry set to 0, knowing that the subsequent data response is CopyBackWriteData\_I.

There is no fixed relationship between credits and particular transactions. If a Requester has received multiple RetryAck responses for different transactions and then receives a credit, there is no fixed credit allocation. The Requester is free to choose the most appropriate transaction from the list of transactions that receives a RetryAck response with that particular Protocol Credit Type.

The Retry mechanism supports up to 16 different credit types. This lets the Completer use different credit types for different resources. For example, a Completer could use one credit type for the resources associated with Read transactions, and another credit type for Write transactions. Using different credit types gives the Completer the ability to efficiently manage its resources by controlling which of the retried requests can be sent again.

The transaction must only be retried by the Requester when a PCrdGrant is received with the correct PCrdType.

> **_NOTE:_** If a Completer is only using one credit type, it is recommended that the PCrdType value of 0b0000 is used. See B2.9.2.2 PCRdType.

A Completer must be able to record all the RetryAck responses to ensure credits are correctly distributed. If the Completer is using more than one credit type, the RetryAck responses that have been given for each credit type must be recorded.

A Requester must limit the number of issued transactions so that the Completer is never required to track more than 1024 transactions that require a PCrdGrant response. This is achieved by limiting the maximum number of outstanding transactions to 1024 for each Requester.

A transaction is outstanding from the cycle that the request is first issued until either:

- The transaction is fully completed, as determined by the return of all the following responses that are expected for the transaction:

    - ReadReceipt
    - CompData
    - RespSepData
    - DataSepResp
    - DBIDResp*
    - Comp, CompCMO, CompPersist, and CompStashDone
    - CompDBIDResp

- RetryAck and PCrdGrant is received and either the request is:

    - Retried using a credit of the appropriate PCrdType and subsequently is fully completed as determined by the return of all responses.
    - Canceled and returns the received credit using the PCrdReturn message.

A Requester can reuse the TxnID value used by a request either:

- As soon as a RetryAck response is received for that request.
- As soon as all the required responses are received for that request if the received responses are Non-RetryAck responses.