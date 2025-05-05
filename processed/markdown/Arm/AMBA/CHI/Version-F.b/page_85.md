Figure B2.11: Dataless transactions

![Image](page_85/image_000000_e2a3b72e5d19ff1ef3b9de214831767f386e5c2f92471b3f1cf9c4bd0b37741e.png)

There are three possible sequences for Dataless transactions.

1. **Transactions without CompAck or Persist**

    The Dataless transactions without CompAck or Persist are:

    - CleanInvalid
    - CleanInvalidPoPA
    - MakeInvalid
    - CleanShared
    - CleanSharedPersist
    - Evict

    The Requester sends the request to the Home.

    The Home returns a completion response, Comp, to the Requester.

2. **Transactions with CompAck**

    The Dataless transactions with CompAck are:

    - CleanUnique
    - MakeUnique