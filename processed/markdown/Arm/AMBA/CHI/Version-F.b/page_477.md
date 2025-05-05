#### B14.5.1.1 Response to new state

When moving to a new state, where the state change has been initiated by the other-side of the interface, a component could be required to change its behavior.

If the state change requires a component to start sending flits or credits, there is no defined limit on the time taken for the component to start the new behavior. This new behavior only occurs in the new state.

If the state change requires a component to stop sending flits or credits, the component is permitted to take some time to respond. In this case, the behavior is observed when first entering a new state which is not expected within that state.

The state change from RUN to DEACTIVATE is the point at which flits and credits stop being sent.

Flits are sent by the Transmitter, which is also the component that determines the state change, and therefore the Transmitter can ensure flits are not sent after the state change.

Credits are sent by the Receiver, but that component does not determine the state change. The Receiver could take some time to react to the state change. Therefore, credits can be sent when first entering the DEACTIV ATE state.

The CHI protocol requires that the Receiver has stopped sending credits and has had all credits returned before signaling the change from DEACTIVATE to STOP.

#### B14.5.1.2 Determining when to move to ACTIVATE or DEACTIVATE

For a given channel, or set of channels in the same direction, the Transmitter is always responsible for initiating the state change from RUN to STOP, or from STOP to RUN.

The Transmitter itself can determine that a state change is needed. This can happen through various mechanisms. The following examples are not exhaustive:

- The Transmitter has flits to send, so must move from STOP to RUN.
- The Transmitter can determine no activity can be performed for a significant period, so can move from RUN to STOP.
- The Transmitter can observe an independent sideband signal indicating a move either from RUN to STOP, or from STOP to RUN.
- The Transmitter can determine that a transaction is not fully complete and therefore the channels should remain in RUN state until all activity has completed.
- The Transmitter can observe a state change on the channel, or set of channels, that are used in the opposite direction. See B14.6 Transmit and receive link interaction.

#### B14.5.1.3 Multiple channels in the same direction

Figure B14.4 shows an example of a multiple channel interface, also referred to as a Link, that transfers payload flits in the same direction. A single pair of LINKACTIVEREQ and LINKACTIVEACK signals are used for all channels.