Home Node (HN) is a node within the interconnect that receives protocol transactions from Request Nodes, completes the required coherency action, and returns a response.

**SN**

Subordinate Node (SN) is a node that receives a Request from a Home Node, completes the required action, and returns a response.

**MN**

Miscellaneous or Misc Node (MN) is a node located within the interconnect that receives DVM messages from Request Nodes, completes the required action, and returns a response.

**IO Coherent node**

A Request Node that generates a subset of Snoopable requests in addition to Non-snoopable requests. The Snoopable requests that an IO Coherent node generates do not result in the caching of the received data in a coherent state. Therefore, an IO Coherent node does not receive any Snoop requests.

**Snoopee**

A Request Node that is receiving a snoop.

**Write-Invalidate protocol**

A protocol in which a Request Node writing to a shared cache line in the system must invalidate all copies before proceeding with the write. The CHI protocol is a Write-Invalidate protocol.

**In a timely manner**

The protocol cannot define an absolute time within which something must occur. A sufficiently idle system can progress and complete without explicit action.

**Inapplicable**

A field value that indicates that the field is not used in the processing of the message.