| subchapter              | subsubchapter                  | page number |
|-------------------------|--------------------------------|-------------|
| B4.11 Hazard conditions |                                | 266         |
|                         | B4.11.1 At the RN-F node       | 266         |
|                         | B4.11.2 At the ICN (HN-F) node | 267         |


## Chapter B6 Interconnect Protocol Flows

| subchapter                      | subsubchapter                                                                           | page number |
|---------------------------------|-----------------------------------------------------------------------------------------|-------------|
| B5.1 Read transaction flows     |                                                                                         | 269         |
|                                 | B5.1.1 Read transactions with DMT and without snoops                                    | 269         |
|                                 | B5.1.2 Read transaction with DMT and with snoops                                        | 270         |
|                                 | B5.1.3 Read transaction with DCT                                                        | 271         |
|                                 | B5.1.4 Read transaction without DMT or DCT                                              | 273         |
|                                 | B5.1.5 Read transaction with snoop response with partial data and no memory update      | 274         |
|                                 | B5.1.6 Read transaction with snoop response with partial data and memory update         | 275         |
|                                 | B5.1.7 ReadOnce* and ReadNoSnp with early Home deallocation                             | 277         |
|                                 | B5.1.8 ReadNoSnp transaction with DMT and separate Non-data and Data-only response      | 277         |
|                                 | B5.1.9 ReadNoSnp transaction with DMT with ordering and separate Non-data and Data-only | 278         |
| B5.2 Dataless transaction flows |                                                                                         | 280         |
|                                 | B5.2.1 Dataless transaction without memory update                                       | 280         |
|                                 | B5.2.2 Dataless transaction with memory update                                          | 281         |
|                                 | B5.2.2 Persistent CMO with snoop and separate Comp and Persist                          | 282         |
|                                 | B5.2.4 Evict transaction                                                                | 283         |
| B5.3 Write transaction flows    |                                                                                         | 285         |
|                                 | B5.3.1 Write transaction with no snoop and separate responses                           | 285         |
|                                 | B5.3.2 Write transaction with snoop and separate responses                              | 286         |
|                                 | B5.3.3 CopyBack Write transaction to memory                                             | 287         |
| B5.4  Atomic transaction flows  |                                                                                         | 289         |
|                                 | B5.4.1 Atomic transactions with data return                                             | 289         |
|                                 | B5.4.2 Atomic transaction without data return                                           | 292         |
|                                 | B5.4.3 Atomic operation executed at the SN                                              | 294         |
| B5.5 Stash transaction flows    |                                                                                         | 297         |
|                                 | B5.5.1 Write with Stash hint                                                            | 297         |
|                                 | B5.5.2 Independent Stash request                                                        | 298         |
| B5.6 Hazard handling examples   |                                                                                         | 299         |
|                                 | B5.6.1 Snoop request                                                                    | 299         |
|                                 | B5.6.2 Request                                                                          | 301         |
|                                 | B5.6.3 Read or Dataless Request                                                         | 303         |
|                                 | B5.6.4 Race hazard                                                                      | 304         |

### Chapter B6 Exclusive accesses

| subchapter                  | subsubchapter                                        | page number |
|-----------------------------|------------------------------------------------------|-------------|
| B6.1 Overview               |                                                      | 306         |
| B6.2 Exclusive monitors     |                                                      | 307         |
|                             | B6.2.1 Snoopable memory location                     | 307         |
|                             | B6.2.2 Additional address comparison                 | 308         |
|                             | B6.2.3 Alternatives to a PoC monitor                 | 308         |
|                             | B6.2.4 Non-snoopable memory location                 | 309         |
| B6.3 Exclusive transactions |                                                      | 310         |
|                             | B6.3.1 Responses to Exclusive requests               | 310         |
|                             | B6.3.2 System responsibilities                       | 312         |
|                             | B6.3.3 Exclusive accesses to Snoopable locations     | 313         |
|                             | B6.3.4 Exclusive accesses to Non-snoopable locations | 314         |

### Chapter B7 Cache Stashing