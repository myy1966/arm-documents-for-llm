#### B11.2.2.1 Suggested DataSource values

Figure B11.1 shows an example multichip configuration and the suggested mapping of DataSource values to different components in the system:

- Each chip in the system has two processors per cluster, with a three-level cache hierarchy.
- The cache in the chip-to-chip interface module is identified as part of the interconnect caches.
- A non-memory component that is not programmed to identify itself as the source of data can return the default value of 0bR0000.

Table B11.1 lists the suggested DataSource encodings.

Table B11.1: Suggested DataSource value encodings

| DataSource[3:0] | DataSource[4] 0, In the local chip                      | DataSource[4] 1, In the remote chip                     |
|-----------------|---------------------------------------------------------|---------------------------------------------------------|
| 0b0000          | Not supported or Completer is not sendng 'useful' value | Not supported or Completer is not sendng 'useful' value |
| 0b0001          | Peer processor cache within local cluster               | -                                                       |
| 0b0010          | Local cluster cache                                     | -                                                       |
| 0b0011          | Interconnect cache                                      | Interconnect cache                                      |
| 0b0100          | Peer cluster caches                                     | Peer cluster caches                                     |
| 0b0101          | -                                                       | -                                                       |
| 0b0110          | PrefetchTgt, memory prefetch was useful                 | PrefetchTgt, memory prefetch was useful                 |
| 0b0111          | PrefetchTgt, memory prefetch was not useful             | PrefetchTgt, memory prefetch was not useful             |
| 0b1000-0b1001   | -                                                       | -                                                       |
| 0b1010          | Local cluster cache, unused prefetch ᵃ                  | -                                                       |
| 0b1011          | Interconnect cache, unused prefetch ᵃ                   | Interconnect cache, unused prefetch ᵃ                   |
| 0b1100-0b1111   | -                                                       | -                                                       |

- ᵃ See B11.3 SLC Replacement Hint.