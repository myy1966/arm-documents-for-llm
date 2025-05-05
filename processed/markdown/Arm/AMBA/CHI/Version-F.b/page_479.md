## B14.6 Transmit and receive link interaction

This section describes the interaction between a link Transmitter and Receiver. It contains the following subsections:

- B14.6.1 Introduction
- B14.6.2 Tx and Rx state machines
- B14.6.3 Expected transitions

### B14.6.1 Introduction

A single component has various different channels, some of which are inputs and some of which are outputs.

For a single component:

- All the channels where the Payload is an output are defined to be the Transmit Link (TXLINK).
- All the channels where the Payload is an input are defined to be the Receive Link (RXLINK).

It is required that the activation and deactivation of the TXLINK and RXLINK are coordinated.

When the TXLINK and RXLINK are both in the stable STOP state:

- If the RXLINK moves to the ACTIVATE state, which is controlled by the component on the other side of the interface, it is required that the TXLINK also moves to the ACTIVATE state, in a timely manner.
- If a component moves the TXLINK to the ACTIVATE state, which is controlled by the component, the RXLINK is expected to also move to the ACTIVATE state, in a timely manner.

When the TXLINK and RXLINK are both in the stable RUN state:

- If the RXLINK moves to the DEACTIVATE state, which is controlled by the component on the other side of the interface, it is required that the TXLINK also moves to the DEACTIVATE state, in a timely manner.
- If a component moves the TXLINK to the DEACTIVATE state, which is controlled by the component, the RXLINK is expected to also move to the DEACTIVATE state, in a timely manner.

When the TXLINK and RXLINK are changing states, the rules about the sending and receiving of credits and flits can be considered independently for each link.

### B14.6.2 Tx and Rx state machines

Figure B14.5 shows the permitted relationships between the Tx and Rx state machines. Figure B14.5 is formatted so that the independent nature of the Tx and Rx state machines can be seen.