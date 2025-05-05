## B14.2 Link layer Credit

This section describes the Link layer Credit (L-Credit) mechanism. Information is transferred across an interface channel by the use of L-Credits. To transfer one flit from the Transmitter to the Receiver, the Transmitter must have obtained an L-Credit.

### B14.2.1 L-Credit flow control

An L-Credit is sent from the Receiver to the Transmitter by asserting the appropriate **LCRDV** signal for a single clock cycle. There is one **LCRDV** signal for each channel. See B13.8 Channel interface signals for the **LCRDV** signal naming for each channel.

Each transfer of a flit from the Transmitter to the Receiver consumes one L-Credit.

The minimum number of L-Credits that a Receiver can provide is 1.

The maximum number of L-Credits thata Receiver can provide is 15.

A Receiver must guarantee that it can accept all the flits for which it has issued L-Credits.

When the link is active, the Receiver must provide L-Credits in a timely manner without requiring any action on the part of the Transmitter.

> **_NOTE:_** An L-Credit cannot be used in the same cycle as being received.