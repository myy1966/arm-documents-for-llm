## B13.3 Flit

A flit is the basic unit of transfer in the Link layer.

Packets are formatted into flits and transmitted across a link. There are two types of flits:

**Protocol flit** A Protocol flit carries a protocol packet in its payload. Every protocol packet is mapped into exactly one protocol flit.

**Link flit** A Link flit carries messages associated with link maintenance. For example, a Transmitter uses a Link flit to return a Link layer Credit, also referred to as an L-Credit, to the Receiver during a link deactivation sequence. Link flits originate at a link Transmitter and terminate at the link Receiver connected at the other side of the link.