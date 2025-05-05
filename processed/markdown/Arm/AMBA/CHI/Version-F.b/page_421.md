- Must make forward progress on the inbound SNP channel without requiring forward progress on outbound REQ channel.
- Permitted, but not required, to wait for forward progress on the outbound RSP channel before making forward progress on the inbound SNP channel.
- Permitted, but not required, to wait for forward progress on the outbound DAT channel before making forward progress on the inbound SNP channel.
- Must make forward progress on the inbound RSP channel without requiring forward progress on any other channel.
- Must make forward progress on the inbound DAT channel without requiring forward progress on any other channel.

> **_NOTE:_** The requirement that a Request Node must make forward progress on the inbound RSP and DAT channel, without requiring forward progress on any other channel, means that a Request Node must be able to accept all Comp and CompData responses for outstanding transactions without sending any CompAck responses.

For a Subordinate Node:

- Permitted, but not required, to wait for forward progress on the outbound RSP channel before making forward progress on the inbound REQ channel.
- Must make forward progress on the inbound REQ channel without requiring forward progress on the outbound DAT channel.
- Must make forward progress on the inbound DAT channel without requiring forward progress on any other channel.