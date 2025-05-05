## B2.1 Channels overview

This section uses shorthand naming for the channels to describe the transaction structure. Table B2.1 shows the shorthand name and the physical channel name that exists on the Request Node or Subordinate Node component.

Communication between nodes is channel-based. Table B2.1 shows the channel naming and the channel designations at the Request Nodes and Subordinate Nodes.

See B13.4 Channel for the mapping of physical channels on the Request Node and Subordinate Node components.

Table B2.1: Channel naming and designation at the Request Node and Subordinate Node

| Channel   | Request Node channel designation | Subordinate Node channel designation |
|-----------|----------------------------------|--------------------------------------|
| REQ       | TXREQ. Outbound Request.                                                         | RXREQ. Inbound Request. |
| WDAT      | TXDAT. Outbound Data. Use for write data, atomic data, snoop data, forward data. | RXDAT. Inbound Data. Use for write data, atomic data. |
| SRSP      | TXRSP. Outbound Response. Use for snoop response and completion acknowledge.     | - |
| CRSP      | RXRSP. Inbound Response. Use for responses from the Completer.                   | TXRSP. Outbound Response. Use for responses from the Completer. |
| RDAT      | RXDAT. Inbound Data. Use for read data, atomic data.                             | TXDAT. Outbound Data. Use for read data, atomic data. |
| SNP       | RXSNP. Inbound Snoop request.                                                    | - |