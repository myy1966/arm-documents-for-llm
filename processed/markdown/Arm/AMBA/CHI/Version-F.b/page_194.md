Table B4.10 – Continued from previous page

| Request          | Initial state <br> UD | Initial state <br> UC | Initial state <br> SD | Initial state <br> SC | Initial state <br> I | Initial state <br> UDP | Initial state <br> UCE |
|------------------|-----------------------|-----------------------|-----------------------|-----------------------|----------------------|------------------------|------------------------|
| CleanInvalid     | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| CleanInvalidPoPA | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |
| MakeInvalid      | -                     | -                     | -                     | -                     | Y                    | -                      | -                      |

#### B4.2.2.5 Cache states for Dataless transactions

This section describes B4.2.2.5.1 Final cache state at the Requester and B4.2.2.5.2 Peer cache state at the completion of a Dataless transaction.

##### B4.2.2.5.1 Final cache state at the Requester

Table B4.11 lists the permitted cache state at the Requester at the completion of the transaction.

Table B4.11: Permitted final Requester cache state

Table B4.10 – Continued from previous page

| Request               | Final state <br> UD | Final state <br> UC | Final state <br> SD | Final state <br> SC | Final state <br> I | Final state <br> UDP | Final state <br> UCE |
|-----------------------|---------------------|---------------------|---------------------|---------------------|--------------------|----------------------|----------------------|
|                       | UD                  | UC                  | SD                  | SC                  | I                  | UDP                  | UCE                  |
| CleanUnique           | Y                   | Y                   | -                   | -                   | -                  | -                    | Y                    |
| MakeUnique            | Y                   | -                   | -                   | -                   | -                  | -                    | -                    |
| Evict                 | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| StashOnceUnique       | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| StashOnceSepUnique    | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| StashOnceShared       | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| StashOnceSepShared    | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| CleanShared           | -                   | Y                   | -                   | Y                   | Y                  | -                    | -                    |
| CleanSharedPersist    | -                   | Y                   | -                   | Y                   | Y                  | -                    | -                    |
| CleanSharedPersistSep | -                   | Y                   | -                   | Y                   | Y                  | -                    | -                    |
| CleanInvalid          | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| CleanInvalidPoPA      | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |
| MakeInvalid           | -                   | -                   | -                   | -                   | Y                  | -                    | -                    |

##### B4.2.2.5.2 Peer cache state

Table B4.12 lists the expected and permitted cache state at the peer Request Node at the completion of the Dataless transaction. In response to a request, the Home must send appropriate snoop to transition cached line at the peer caches to either expected or permitted final states.