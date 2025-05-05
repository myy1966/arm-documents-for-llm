Table B14.4 Continued from previous page

| Route  | State 1       | State 2      | State 3     | State 4     |
|--------|---------------|--------------|-------------|-------------|
| Path 2 | TxStop/RxStop | TxAct/RxStop | TxRun/RxAct | TxRun/RxRun |

#### B14.6.3.2 Expected transitions from TxRun/RxRun to TxStop/RxStop

A transition from a Run/Run state to a Stop/Stop state requires that L-Credits are returned. A link must remain in the DEACTIVATE state until all L-Credits are returned.

There are four expected routes from a stable Run/Run to Stop/Stop state.

Table B14.5 shows, in terms of the state transitions, the four expected paths.

Table B14.5: State 5

| Route  | State 1     | State 2       | State 3         | State 4        | State 5       |
|--------|-------------|---------------|-----------------|----------------|---------------|
| Path 1 | TxRun/RxRun | TxDeact/RxRun | TxDeact/RxDeact | TxStop/RxDeact | TxStop/RxStop |
| Path 2 | TxRun/RxRun | TxDeact/RxRun | TxDeact/RxDeact | TxDeact/RxStop | TxStop/RxStop |
| Path 3 | TxRun/RxRun | TxRun/RxDeact | TxDeact/RxDeact | TxStop/RxDeact | TxStop/RxStop |
| Path 4 | TxRun/RxRun | TxRun/RxDeact | TxDeact/RxDeact | TxDeact/RxStop | TxStop/RxStop |

#### B14.6.3.3 Transitions around a stable state

It is permitted, but not expected, to transition around a stable TxRun/RxRun or TxStop/RxStop state.

In the majority of cases, moving to the stable Run/Run or Stop/Stop state would be expected.

The most likely use case for wanting to move quickly out of one of the stable states is when an interface has started to enter a low power state, but there is still some activity required. For example, the low power state could have been entered prematurely, or some new activity arose, by coincidence, while the low power state was being entered. In this use case, it is desirable to be able to move back to the Run/Run state as quickly as possible.

#### B14.6.3.4 Asynchronous race condition

There are situations where two output signals, X and Y, have a defined relationship such that:

- Output X must change after or at the same time as output Y, but it is not permitted to change before output Y.

This relationship applies specifically as follows:

- The assertion of RXACK must not occur before the assertion of TXREQ.
- The deassertion of RXACK must not occur before the deassertion of TXREQ.
- The assertion of TXREQ must not occur before the deassertion of RXACK.
- The deassertion of TXREQ must not occur before the assertion of RXACK.

In Figure B14.5, these transitions are labeled as Banned Output Race and the resultant state is shown in red.

It is possible to observe these states if monitoring the output signals at a point in the system where asynchronous race conditions can result in two signals, that are asserted within the same cycle, are observed in different clock cycles.

A component that is on the other side of the interface, and has the two signals as inputs, can see the state transition if an asynchronous input race occurs. These transitions are labeled on the diagram as Aysnc Input Race and the resultant state is shown in yellow.