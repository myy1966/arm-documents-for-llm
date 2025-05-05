Each transaction request includes a QoS value which can be used by the Completer to influence the allocation of credits as resources become available. See B11.1 Quality of Service (QoS) mechanism for further details.

### B2.9.1 Credit Return

It is possible for a Requester to be given more credits than required.

This specification does not define when this can occur, but two typical scenarios are:

- A transaction is canceled between the first attempt and the point at which the request can be resent with P-Credit.
- A transaction is requested multiple times with increasing QoS values. However, only a single completion of the transaction is required.

> **_NOTE:_** If a Requester makes a second request before the first request has received a RetryAck response, both transactions must be acceptable to occur. However, as an example, this behavior would typically not be acceptable for accesses to a peripheral device.

A Requester returns a credit by the use of the PCrdReturn transaction. This is effectively a No Operation transaction that uses the credit that is not required. This transaction is used to inform the Completer that the allocated resources are no longer required for the given PCrdType.

Any credits that are not required must be returned in a timely manner.

> **_NOTE:_** Any unused pre-allocated credit must be returned to avoid components holding on to credits in expectation of using them later. Such behavior is likely to result in an inefficient use of resources and to make analysis of the system performance difficult.

### B2.9.2 Transaction Retry mechanism

The following sections describe the Request transaction fields used by the Retry mechanism.

The transaction retry mechanism is not applicable to the PrefetchTgt transaction.

### B2.9.2.1 AllowRetry

The AllowRetry field indicates if the Request transaction can be given a RetryAck response. See Table B13.25 for the AllowRetry value encodings. The AllowRetry field must be asserted the first time a transaction is sent.

The AllowRetry field must be deasserted when either:

- The transaction is using a pre-allocated P-Credit.
- The transaction is PrefetchTgt.

### B2.9.2.2 PCRdType

The PCrdType field indicates the credit type associated with the request and is determined as follows:

- For a Request transaction:

    - If the AllowRetry field is asserted, the PCrdType field must be set to 0b0000.