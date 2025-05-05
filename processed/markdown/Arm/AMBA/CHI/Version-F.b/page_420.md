## B13.4 Channel

The Link layer provides a set of channels for flit communication.

Each channel has a defined flit format that has multiple fields and some of the field widths have multiple possible values. In some cases, the defined flit format can be used on both an inbound and an outbound channel.

Table B13.1 shows the channels, and the mapping onto the Request Node and Subordinate Node component channels.

Table B13.1: Channels' mapping onto the Request Node and Subordinate Node component channels

| Channel      | Description                                                                                                                                                                   | Usage                                                  | Request Node channel | Subordinate Node channel |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|----------------------|--------------------------|
| REQ Request  | The request channel transfers flits associated with request messages such as Read requests and Write requests. See B13.8.1 Request, REQ, channel.                             | All Requests                                           | TXREQ                | RXREQ                    |
| RSP Response | The response channel transfers flits associated with response messages that do not have a data payload such as write completion messages. See B13.8.2 Response, RSP, channel. | Responses from the Completer                           | RXRSP                | TXRSP                    |
| RSP Response | The response channel transfers flits associated with response messages that do not have a data payload such as write completion messages. See B13.8.2 Response, RSP, channel. | Snoop Response and Completion Acknowledge              | TSRSP                | -                        |
| SNP Snoop    | The snoop channel transfers flits associated with Snoop and SnpDVMOp Request messages. See B13.8.3 Snoop, SNP, channel.                                                       | All Snoop requests                                     | RSRSP                | -                        |
| DAT Data     | The data channel transfers flits associated with protocol messages that have a data payload such as read completion and WriteData messages. See B13.8.4 Data, DAT, channel.   | WriteData, and Snoop response data from a Request Node | TXDAT                | RXDAT                    |
| DAT Data     | The data channel transfers flits associated with protocol messages that have a data payload such as read completion and WriteData messages. See B13.8.4 Data, DAT, channel.   | Read data                                              | RXDAT                | TXDAT                    |

### B13.4.1 Channel dependencies

The following dependencies are permitted between the channels in the protocol.

For a Request Node: