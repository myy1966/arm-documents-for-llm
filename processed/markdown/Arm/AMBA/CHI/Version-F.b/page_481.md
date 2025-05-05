- There are a few cases where, by coincidence, a state change occurs due to two events, one on each side of the link, occurring at the same time. This is always a diagonal path and is shown by a black arrow.
- The stub-lines show dead-end paths where an exit from a state is not permitted. The color of a stub-line indicates which agent is responsible for ensuring that the path is not taken.
- The TxStop/RxStop and TxRun/RxRun states are expected to be stable states, and are typically the states where the state machines stay for long periods of time. These states are highlighted with a bold outline. All other states are considered transient states that are exited in a timely manner.
- The gray states, on the bottom right of Figure B14.5, are replications of those on the top left. They are shown to aid clarity and maintain the symmetry of the diagram.
- The yellow states can only be reached by observing a race between two input signals. The transition into these states is labeled with Async Input Race. See B14.6.3.4 Asynchronous race condition.
- The red states can only be reached by observing a race between two output signals. A race between two outputs is not permitted at the edge of a component and therefore the transition into these states is labeled with Banned Output Race. These states can only be observed at a midpoint between two components. See B14.6.3.4 Asynchronous race condition.
- The bold arrows are used to indicate the expected transitions around the state machine. These are described in more detail in B14.6.3 Expected transitions.
- The arrows labeled Permitted are state transactions that would not normally be expected, but they are permitted by the protocol.

#### B14.6.2.1 State naming

Figure B14.5 shows the full set of states, including those that can only be reached through race conditions. A more detailed discussion of race conditions can be found in B14.6.3.4 Asynchronous race condition.

There are two different TxStop/RxRun states and two different TxRun/RxStop states. These states differ in how they are reached and the permitted ways to exit from them. To differentiate between these states, a [+] suffix is used to indicate which state machine, Tx or Rx, is running ahead. For example:

- TxStop/RxRun+ indicates that the Tx state machine has remained in the previous STOP state, while the Rx state machine has advanced to the next RUN state.
- TxStop+/RxRun indicates that the Tx state machine has advanced to the next STOP state, while the Rx state machine remains in the previous RUN state.

### B14.6.3 Expected transitions

Figure B14.6 shows the expected state transitions.

The annotations on the diagram arrows in Figure B14.6 are:

**Local Initiate** Indicates that the local agent has initiated the process of leaving one stable state towards the other stable state.

**Remote Initiate** Indicates that the remote agent on the other side of the interface has initiated the process of leaving one stable state towards the other stable state.