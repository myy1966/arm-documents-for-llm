    - If the agent is the original Requester of the transaction, dependencies are described for each input to that agent.
    - If the agent is not the original Requester of the transaction, dependencies are described for each input to that agent after the first input that agent received. Every output is considered dependent on the first input.
    - This section does not describe all dependencies across different transactions, even when they are both to the same address. See B2.6 Ordering and B4.11 Hazard conditions.

The conventions used to describe actions in this section are:

**Issues**

Used only for the first message in a transaction, for example: The Requester issues a WriteNoSnp request...

**Sends**

A message sent by an agent in a direction away from the Requester.

**Sends a downstream**

A message relayed by an intermediate agent in a direction away from the Requester, for example:

The Home sends a downstream Read request to the Subordinate.

**Returns**

A message sent by an agent in a direction towards the Requester.

**Provides**

A message sent by an agent in response to a snoop, for example:

...provides a snoop response.

**Permitted, but not required**

The action is not encouraged nor discouraged, and is compliant in either case.

**Not permitted**

The action described would cause non-compliance to the specification. For example:

The Home is not permitted to wait for...before sending...

### B2.3.1 Read transactions

Read transactions are grouped into the following types:

- B2.3.1.1 Allocating Read
- B2.3.1.2 Non-allocating Read

#### B2.3.1.1 Allocating Read

Figure B2.1 shows the possible transaction flows for an Allocating Read transaction.