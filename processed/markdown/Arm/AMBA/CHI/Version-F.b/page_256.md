    - Passing Exclusive read transactions

    > **_NOTE:_** Exclusive read transactions that fail due to Non-exclusive support for the address range being accessed are treated as corresponding Non-exclusive reads, Home can therefore use Forwarding type snoops in these cases.

For the rules that are specific to a particular Forwarding snoop see the individual sub-sections in B4.8.3 Forwarding Snoop transactions.

The tables in the following individual sub-sections show the Snoopee state transitions and the corresponding responses to the Requester and the Home.

The first column in the tables shows the initial cache state, and is the combined data and tag state. Table B4.53 shows the combined state used and the corresponding data and possible tag state combinations.

Table B4.53: Combined state and the corresponding data and tag states

| Combined state | Data state | Tag state |
|----------------|------------|-----------|
| I              | I          | I         |
| UC             | UC         | I         |
| UC             | UC         | Clean     |
| UCE            | UCE        | I         |
| UD             | UD         | I         |
| UD             | UD         | Clean     |
| UD             | UD         | Dirty     |
| UDP            | UDP        | I         |
| SC             | SC         | I         |
| SC             | SC         | Clean     |
| SD             | SD         | I         |
| SD             | SD         | Clean     |
| SD             | SD         | Dirty     |

The last three columns in the tables correspond to the TagOp value in the Data responses to Home. They are organized, based on the initial state of the tags:

**Dirty** Two columns:

-  First column: Indicates if the transition itself is permitted or not. This column is only relevant when the tag initial state is Dirty. Table B4.54 shows the conventions used, P and NP are only relevant when the data initial state is UD or SD and the tag initial state is Dirty.