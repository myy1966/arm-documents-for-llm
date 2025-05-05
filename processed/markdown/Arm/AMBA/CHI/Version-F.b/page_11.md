


| subchapter | subsubchapter               | page number |
|------------|-----------------------------|-------------|
|            | B10.3.2 Remote invalidation | 375         |
| B10.4 DVM  |                             | 376         |
| B10.5 MPAM |                             | 377         |

### Chapter B11 System Control, Debug, Trace, and Monitoring

| subchapter                               | subsubchapter                                           | page number |
|------------------------------------------|---------------------------------------------------------|-------------|
| B11.1 Quality of Service (QoS) mechanism |                                                         | 379         |
|                                          | B11.1.1 Overview                                        | 379         |
|                                          | B11.1.2 QoS priority value                              | 379         |
|                                          | B11.1.3 Repeating a transaction with a higher QoS value | 379         |
| B11.2 Data Source indication             |                                                         | 380         |
|                                          | B11.2.1 DataSource value assignment                     | 380         |
|                                          | B11.2.2 Crossing a chip-to-chip interface               | 380         |
|                                          | B11.2.3 Example use cases                               | 382         |
| B11.3 SLC Replacement Hint               |                                                         | 383         |
|                                          | B11.3.1 Characteristics                                 | 383         |
| B11.4 MPAM                               |                                                         | 385         |
|                                          | B11.4.1 MPAMSP                                          | 385         |
|                                          | B11.4.2 MPAM value propagation                          | 386         |
|                                          | B11.4.3 Stash transaction rules                         | 386         |
|                                          | B11.4.4 Request to Subordinate rules                    | 386         |
| B11.5 Page-based Hardware Attributes     |                                                         | 387         |
|                                          | B11.5.1 PBHA field applicability                        | 387         |
|                                          | B11.5.2 Interconnect use of PBHA                        | 387         |
|                                          | B11.5.3 Stash transaction rules                         | 387         |
|                                          | B11.5.4 PBHA value consistency                          | 387         |
| B11.6 Completer Busy                     |                                                         | 389         |
|                                          | B11.6.1 Use case 389                                    | 389         |
| B11.7 Trace Tag                          |                                                         | 391         |
|                                          | B11.7.1 TraceTag usage and rules                        | 391         |

### Chapter B12 Memory Tagging

| subchapter                                   | subsubchapter                                     | page number |
|----------------------------------------------|---------------------------------------------------|-------------|
| B12.1 Introduction                           |                                                   | 394         |
| B12.2 Message extensions                     |                                                   | 395         |
| B12.3 Tag coherency                          |                                                   | 396         |
| B12.4   Read transaction rules               |                                                   | 397         |
|                                              | B12.4.1 TagOp values                              | 397         |
|                                              | B12.4.2 Permitted initial MTE tag states          | 399         |
| B12.5 Write transactions                     |                                                   | 401         |
|                                              | B12.5.1 Permitted TagOp values                    | 401         |
|                                              | B12.5.2 TagOp, TU, and tags relationship          | 401         |
| B12.6 Dataless transactions                  |                                                   | 403         |
| B12.7 Atomic transactions                    |                                                   | 404         |
| B12.8 Stash transaction                      |                                                   | 405         |
| B12.9 Snoop requests                         |                                                   | 406         |
|                                              | B12.9.1 Non-forwarding snoops                     | 406         |
|                                              | B12.9.2 Forwarding snoops                         | 406         |
|                                              | B12.9.3 Stash snoops                              | 407         |
|                                              | B12.9.4 Permitted TagOp values in Snoop responses | 407         |
| B12.10 Home to Subordinate transactions      |                                                   | 409         |
| B12.11 Error response                        |                                                   | 410         |
|                                              | B12.11.1 Tag Match                                | 410         |
|                                              | B12.11.2 Non-Tag Match errors                     | 410         |
|                                              | B12.11.3 MTE not supported                        | 411         |
| B12.12 Requests and permitted tag operations |                                                   | 412         |
| B12.13 TagOp field use summary               |                                                   | 414         |