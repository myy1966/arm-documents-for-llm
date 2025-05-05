## B9.1 Packet level

This section describes the errors at the packet level. It contains the following sections:

- B9.1.1 Error types
- B9.1.2 Error response fields

### B9.1.1 Error types

There are two types of error reporting at packet level.

The packet level error reporting types are:

**Data Error, DERR**

Used when the correct address location has been accessed, but an error is detected within the data. Typically, this is used when data corruption has been detected by Error Correction Code (ECC) or a parity check. Data Error reporting is supported by the RespErr, Poison, and DataCheck fields in the DAT packet. When processing of a request received by Home that is required to be propagated to the Subordinate results in a DERR, the Home must not stop propagating the request to the Subordinate.

> **_NOTE:_** An error in data being evicted from Home, or received in a Snoop response as a result of the request, are examples of the request resulting in a DERR.

**Non-data Error, NDERR**

Used when an error is detected that is not related to data corruption. This specification does not define all cases when this error type is reported. Typically, this error type is reported for:

- An attempt to access a location that does not exist.
- An illegal access, such as a write to a read-only location.
- An attempt to use a transaction type that is not supported.

Non-data Error reporting is supported by the RespErr field in the RSP and DAT packets. When processing of a request received by Home results in an NDERR, it is permitted, but not required, to propagate the request to the Subordinate. The Home is required to pass-back the NDERR in the response to the Requester.

### B9.1.2 Error response fields

The RespErr field is used to indicate error conditions. The RespErr field is included in both response and data packets.

Table B9.1 shows the encoding of the RespErr field. See B6.3.1 Responses to Exclusive requests for more details on the Exclusive Okay response.