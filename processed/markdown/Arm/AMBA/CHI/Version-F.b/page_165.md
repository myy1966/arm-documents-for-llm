## B2.9 Request Retry

A Request Retry mechanism ensures that when a request reaches a Completer, the request can be either be accepted or be given a RetryAck response. Request Retry prevents blocking the REQ channel. There is no mechanism to Retry messages on the DAT, RSP, or SNP channels. For example, a DataPull response to a stash snoop cannot be retried.

Request Retry is not applicable to the PrefetchTgt transaction. The PrefetchTgt transaction cannot be retried because there is no response associated with this request.

A Requester is required to hold all the details of the request until a response is received indicating that the request has either been accepted or must be sent again at a later point in time. To meet this requirement, except for PrefetchTgt, the AllowRetry field must be asserted the first time a transaction is sent.

A Completer that is receiving requests is able to give a RetryAck response to a request that cannot be accepted. Typically, a Completer with limited resources and insufficient storage to hold the current request until some earlier transactions have completed will provide a RetryAck response.

The Completer is responsible for recording where the request came from RetryAck response is given, as determined by the SrcID of the request. The Completer is also responsible for determining and recording the type of Protocol Credit (P-Credit) required to process the request. The PCrdType field in the RetryAck encodes the type of P-Credit that is granted by the Completer. When required resources become available, at a later point in time, the Completer must subsequently send a P-Credit to the Requester, using a PCrdGrant response. The PCrdGrant response indicates to the Requester that the transaction can be retried.

> **_NOTE:_** There is no explicit mechanism to request a credit. A transaction that is given a RetryAck response implicitly requests a credit.

Responses could be reordered so PCrdGrant is received by the Requester before the RetryAck response for the transaction is received. In this case, the Requester must record the received credit, including the credit type. The credit can appropriately be assigned by the Requester when the RetryAck response is received.

> **_NOTE:_** Typically, the delay between a RetryAck and PCrdGrant response is much longer than any delay caused by interconnect reordering. PCrdGrant is expected to rarely be reordered with respect to RetryAck.

When the Requester receives a credit, the request can be resent in a second attempt with a credit allocation indication. The credit allocation indication is performed by deasserting the AllowRetry field. The second attempt to carry out the transaction is guaranteed to be accepted.

The transaction that is resent must have the same field values as the original request, except when the field is inapplicable or is one of the following:

- QoS
- TgtID, see B3.3.1 TgtID determination for Request messages.
- TxnID
- ReturnTxnID for:

    - ReadNoSnp and ReadNoSnpSep from the Home Node to the Subordinate Node, and a DMT flow is not being used.
    - WriteNoSnp or Combined Write from the Home Node to the Subordinate Node, and a DWT flow is not being used.

- SLCRepHint
- AllowRetry, which must be deasserted
- PCrdType, which must be set to the value in the Retry response for the original transaction.