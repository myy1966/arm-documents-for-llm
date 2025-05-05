## B14.3 Low power signaling

This section describes the signaling used to enhance the low power operation of the interface. There are several different levels of operation:

**Flit Level Clock Gating**

This technique is used to provide a cycle-by-cycle indication of the activity of each of the channels of the interface. For each channel, an additional signal is provided to indicate if a transfer could occur in the following cycle. This signaling permits local clock gating of certain registers associated with the interface.

**Link Activation**

Link activation and deactivation are supported to permit the interface to be taken to a safe state, so that both-sides of the interface can enter a low power state that permits them to be either clock-gated or power-gated.

**Protocol Activity Indication**

The Protocol layer activity indication is used by components to indicate if there are ongoing transactions in progress. The Protocol layer activity indication can be used to influence the decision to use other low power techniques.
