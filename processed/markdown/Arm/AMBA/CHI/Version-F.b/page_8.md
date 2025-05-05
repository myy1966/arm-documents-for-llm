| subchapter         | subsubchapter                                                   | page number |
|--------------------|-----------------------------------------------------------------|-------------|
|                    | B2.8.5 Size, Address, and Data alignment in Atomic transactions | 157         |
|                    | B2.8.6 Critical Chunk Identifier                                | 159         |
|                    | B2.8.7 Critical Chunk First Wrap order                          | 160         |
|                    | B2.8.8 Data Beat ordering                                       | 160         |
|                    | B2.8.9 Data transfer examples                                   | 161         |
| B2.9 Request Retry |                                                                 | 165         |
|                    | B2.9.1 Credit Return                                            | 167         |
|                    | B2.9.2 Transaction Retry mechanism                              | 167         |
|                    | B2.9.3 Transaction Retry flow                                   | 168         |

### Chapter B3 Network Layer

| subchapter                        | subsubchapter                                             | page number |
|-----------------------------------|-----------------------------------------------------------|-------------|
| B3.1 System Address Map, SAM      |                                                           | 171         |
| B3.2 Node ID                      |                                                           | 172         |
| B3.3 TgtID determination          |                                                           | 173         |
|                                   | B3.3.1 TgtID determination for Request messages           | 173         |
|                                   | B3.3.2 TgtID determination for Response messages          | 173         |
|                                   | B3.3.3 TgtID determination for snoop request messages     | 174         |
| B3.4 Network layer flow examples. |                                                           | 175         |
|                                   | B3.4.1 Simple flow                                        | 175         |
|                                   | B3.4.2 Flow with interconnect-based SAM                   | 175         |
|                                   | B3.4.3 Flow with interconnect-based SAM and Retry request | 176         |

### Coherence Protocol

| subchapter                                                 | subsubchapter                                          | page number |
|------------------------------------------------------------|--------------------------------------------------------|-------------|
| B4.1 Cache line states                                     |                                                        | 179         |
|                                                            | B4.1.1 Empty cache line ownership                      | 180         |
|                                                            | B4.1.2 Ownership of cache line with partial Dirty data | 180         |
| B4.2 Request types                                         |                                                        | 181         |
|                                                            | B4.2.1 Read transactions                               | 181         |
|                                                            | B4.2.2 Dataless transactions                           | 187         |
|                                                            | B4.2.3 Write transactions                              | 195         |
|                                                            | B4.2.4 Combined Write requests                         | 201         |
|                                                            | B4.2.5 Atomic transactions                             | 204         |
|                                                            | B4.2.6 Other transactions                              | 210         |
| B4.3 Snoop request types                                   |                                                        | 212         |
| B4.4 Request transactions and corresponding Snoop requests |                                                        | 215         |
|                                                            | B4.4.1 Number of snoops to send                        | 215         |
|                                                            | B4.4.2 Selection of snoop to send                      | 215         |
| B4.5 Response types                                        |                                                        | 219         |
|                                                            | B4.5.1 Completion response                             | 219         |
|                                                            | B4.5.2 WriteData response                              | 222         |
|                                                            | B4.5.3 Snoop response                                  | 224         |
|                                                            | B4.5.4 Miscellaneous response                          | 229         |
| B4.6 Silent cache state transitions                        |                                                        | 233         |
| B4.7 Cache state transitions at a Requester                |                                                        | 235         |
|                                                            | B4.7.1 Read request transactions                       | 235         |
|                                                            | B4.7.2 Dataless request transactions                   | 243         |
|                                                            | B4.7.3 Write request transactions                      | 244         |
|                                                            | B4.7.4 Atomic transactions                             | 246         |
|                                                            | B4.7.5 Other request transactions                      | 247         |
| B4.8 Cache state transitions at a Snoopee                  |                                                        | 248         |
|                                                            | B4.8.1 Non-Forwarding and Non-stash Snoop transactions | 248         |
|                                                            | B4.8.2 Stash Snoop transactions                        | 253         |
|                                                            | B4.8.3 Forwarding Snoop transactions                   | 255         |
| B4.9 Returning Data with Snoop response                    |                                                        | 264         |
| B4.10 Do not transition to SD                              |                                                        | 265         |