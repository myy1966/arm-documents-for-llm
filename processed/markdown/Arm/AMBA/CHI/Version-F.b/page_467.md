## B13.11 Link flit

A link flit is used to return L-Credits to the receiver during a link deactivation sequence. Link flits originate at a link Transmitter and terminate at the link Receiver on the other side of the link.

A link flit is identified by a zero value in the Opcode field. The TxnID field of the link flit is required to be 0. The remaining fields are not used and can take any value. See B13.10.18 Channel opcodes, Opcode for the link flit type encoding.