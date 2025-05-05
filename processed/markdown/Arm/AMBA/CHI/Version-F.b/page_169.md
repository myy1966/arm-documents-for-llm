3. The HN-F sends a P-Credit, using the PCrdGrant response, when a resource has been allocated for the transaction.
- The PCrdGrant includes the PCrdType allocated for the original request.
4. The RN-F re-sends the ReadOnce transaction with AllowRetry deasserted.
- The request uses the P-Credit and sets the PCrdType field to the value allocated for the original request.

It is permitted, but not expected, for a Completer to send a PCrdGrant before the associated RetryAck response is sent.

> **_NOTE:_** The Requester could receive PCrdGrant before RetryAck.

The transaction must not be resent until both a RetryAck response and an appropriate P-Credit is received for the transaction.