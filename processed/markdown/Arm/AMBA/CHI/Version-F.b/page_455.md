### B13.10.32 Endian

This field indicates the endianness of Data in an Atomic transaction. See B2.8.5.3 Endianness.

Applicable in Atomic requests, inapplicable in all other requests and must be set to 0.

Table B13.24 shows the Endian value encodings.

Table B13.24: Endian value encodings

| Endian | Description   |
|--------|---------------|
| 0      | Little Endian |
| 1      | Big Endian    |

### B13.10.33 Allow Retry, AllowRetry

This field specifies that the request is being sent without a P-Credit and that the target can determine if a retry response is given. See B2.9.2 Transaction Retry mechanism.

Table B13.25 shows the AllowRetry value encodings.

Table B13.25: AllowRetry value encodings

| AllowRetry | Description                     |
|------------|---------------------------------|
| 0          | RetryAck response not permitted |
| 1          | RetryAck response permitted     |

### B13.10.34 Expect Completion Acknowledge, ExpCompAck

This field indicates that the transaction includes a CompAck response.

Table B13.26 shows the ExpCompAck value encodings.

Table B13.26: ExpCompAck value encodings

| ExpCompAck | Description                                     |
|------------|-------------------------------------------------|
| 0          | Transaction does not include a CompAck response |
| 1          | Transaction includes a CompAck response         |

For CopyBack Write transactions, when ExpCompAck cannot be used in isolation to determine if a CompAck is included in the transaction. The transaction flow selected by Home determines if a CompAck is required. See B2.3.2.3 CopyBack Write for more information.