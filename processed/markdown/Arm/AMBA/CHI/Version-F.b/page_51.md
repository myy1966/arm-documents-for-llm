## B2.3 Transaction structure

This section describes the ways that a transaction can complete. This section describes all the permitted options that can be used by the various components that participate in a transaction.

All transaction types, except PCrdReturn and PrefetchTgt, can have a Retry sequence at the start of the transaction. For ease of presentation, the Retry sequence is described separately, see B2.3.8 Retry.

Other independent transactions may need to be performed to complete certain transactions, such as a snoop or memory transaction. These transactions are described separately in the later section, B2.3.9 Home Initiated transactions.

Some transactions from Home to Subordinate support the use of a separate ReturnNID and ReturnTxnID field, which allow certain responses to be returned to the original Requester rather than the Home. It is permitted, but not required, to set the ReturnNID and ReturnTxnID fields, such that they are equal to the SrcID and TxnID. This means all responses are returned to the Home. In this instance, the transaction from Home to Subordinate is considered as if it were an independent transaction. See B2.3.9 Home Initiated transactions for more details.

Typically, a field or opcode in the request determines whether a particular message can be included in the transaction flow, described as Optional. Optional messages do not express whether a sender chooses to send the message.

The term Requester is always used to refer to the original Requester of a transaction in this section. Requester does not refer to an intermediate agent that issues a secondary request to complete the original transaction. The term Requester always refers to a Request Node, RN-F, RN-I, or RN-D.

In this section, a diagram with an arrow containing multiple message labels indicates any one of the messages can be sent in a flow. Requirements of when a particular message can be used in the transaction flow can be derived from elsewhere in the specification.

The flows described in this section are intended to include a complete description of the messages that can be included in a transaction flow. The following is not included:

- The channel that is used for a particular transaction.
- A description of when a transaction can be issued or what the reason is for using a particular transaction.
- A description of which combinations of fields can be used in a request. Request fields are only highlighted when they affect the options for completing a transaction.

Dependencies described in this section use the following approach:

- An implicit dependency exists for each component when first participating in a transaction sequence. Except for the original Requester, any other component must receive a first message associated with a transaction before any subsequent messages are sent for that transaction.
- Where a component sends multiple messages associated with the same transaction, the messages are assumed to be sent in any order. The messages are also assumed to be received in any order, unless an explicit dependency is described.
- Data transfers are shown in the diagrams as a single message. This message can consist of multiple data transfers, see B2.8 Data transfer for more details. Where a dependency is described, the dependency is from the first data transfer received, except when the dependency is explicitly stated to be different.
- Where a required or permitted dependency exists in one direction between two components, a dependency in the opposite direction is not permitted. The text in this section only describes the dependency in one direction.
- The amount of detail in a dependency rule is context dependent. When the source of the dependency and what is dependent is obvious, the agents are not included.
- For any agent that has one or more outputs: