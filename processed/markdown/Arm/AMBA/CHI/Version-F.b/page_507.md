- At the endpoint.

For Snoopable transactions, the interconnect can either:

- Perform the atomic operation required by an Atomic transaction within the interconnect. This requires that the interconnect performs the appropriate Read, Write, and Snoop transactions to complete the Atomic transaction.
- If the appropriate endpoint Subordinate is configured to indicate support of Atomic transactions, the interconnect can pass the Atomic transaction to the Subordinate. The interconnect is still required to perform the appropriate Snoop and Write transactions before issuing the Atomic transaction to the Subordinate.

### B16.3.3 Subordinate Node support

Subordinate Node support for Atomic transactions is optional.

The Atomic\_Transactions property is used to indicate that a Subordinate Node supports Atomic transactions.

If a Subordinate Node supports Atomic transactions for particular memory types, or for particular address regions, when receiving an unsupported Atomic transaction, the Subordinate Node must give an appropriate Error response.