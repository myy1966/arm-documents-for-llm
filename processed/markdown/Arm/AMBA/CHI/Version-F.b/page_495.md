## B16.1 Interface properties and parameters

A property is used to declare a capability.

The properties and parameters that specify the interface behavior are described in the following sections:

- B16.1.1 Atomic\_Transactions
- B16.1.2 Cache\_Stash\_Transactions
- B16.1.3 Direct\_Memory\_Transfer
- B16.1.4 Data\_Poison
- B16.1.5 Direct\_Cache\_Transfer
- B16.1.6 Data\_Check
- B16.1.7 Check\_Type
- B16.1.8 CleanSharedPersistSep\_Request
- B16.1.9 MPAM\_Support
- B16.1.10 CCF\_Wrap\_Order
- B16.1.11 Req\_Addr\_Width
- B16.1.12 NodeID\_Width
- B16.1.13 Data\_Width
- B16.1.14 Enhanced\_Features
- B16.1.15 Deferrable\_Write
- B16.1.16 RME\_Support
- B16.1.17 Nonshareable\_Cache\_Maint
- B16.1.18 PBHA\_Support
- B16.1.19 DVM\_Support

### B16.1.1 Atomic\_Transactions

An Atomic\_Transactions property is used to indicate if a component supports Atomic transactions.

Table B16.1 shows the Atomic\_Transactions property options.

Table B16.1: Atomic\_Transactions property options

| Atomic\_Transactions value | Description                            |
|----------------------------|----------------------------------------|
| True                       | Atomic transactions are supported.     |
| False or Not specified     | Atomic transactions are not supported. |

A component that supports Atomic transactions must support all Atomic transactions. However, it is not required that a component that supports Atomic transactions supports the targeting of all memory types. See B16.3 Atomic transaction support.

### B16.1.2 Cache\_Stash\_Transactions

A Cache\_Stash\_Transactions property is used to indicate if a component supports Cache Stashing transactions.

Table B16.2 shows the Cache\_Stash\_Transactions propety options.