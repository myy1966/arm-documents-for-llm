When read data or write data is reordered by the interconnect, the CCID field permits quick identification of the most critical bytes within a transaction by comparing the CCID value with the DataID value. When the two values match, the data bytes being transferred are the critical bytes.

The bits to match is dependent on the data bus width:

- For a data bus width of 128 bits, the CCID and DataID bits must match for the critical chunk.
- For a data bus width of 256 bits only the most significant CCID and DataID bits must match for the critical chunk.

### B2.8.7 Critical Chunk First Wrap order

The Sender of Data is permitted, but not required, to send individual Data packets of a transaction in critical chunk first wrap order.

The interface property, CCF\_Wrap\_Order defines the capabilities of a Sender, and the guarantees provided by the Receiver:

- CCF\_Wrap\_Order at the Sender:

    **True** The Sender signals the Data packets can be sent in critical chunk first wrap order.

    **False** The Sender signals the Data packets cannot be sent in critical chunk first wrap order.

- CCF\_Wrap\_Order at the interconnect:

    **True** The interconnect signals the Data packets are guaranteed to maintain the order that transactions are received.

    **False** The interconnect signals the Data packets are not guaranteed to maintain the order that transactions are received.

- CCF\_Wrap\_Order at the Receiver that is not an interconnect:

    **True** The Receiver requires the Data packets to be received in critical chunk first wrap order.

    **False** The Receiver does not require the Data packets to be received in critical chunk first wrap order.

If some components in the system do not support sending Data packets in critical chunk first wrap order, the receiver of Data must not rely on Data being received in critical chunk first wrap order.

> **_NOTE:_** At design time, the CCF\_Wrap\_Order parameter can help a component to identify if Data packets need to be sent in critical chunk first wrap order. For example, if the component is aware to be connected to an out-of-order interconnect, its Data packet path could be simplified by not returning the Data packets in critical chunk first wrap order.
>
> If the interconnect has the CCF\_Wrap\_Order property set to True, a component interfacing to that interconnect can send Data packets in critical chunk first wrap order, if capable. The Receiver can subsequently make use of possible latency optimization, due to receiving the critical chunk first.

### B2.8.8 Data Beat ordering

The reordering of data packets within a transaction is permitted when passing across an interconnect. However, the original source of data packets is permitted, but not required, to provide the packets in a critical chunk first, wrap order. See B2.8.7 Critical Chunk First Wrap order.