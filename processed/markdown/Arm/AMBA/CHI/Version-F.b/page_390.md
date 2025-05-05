Table B11.6: Prefetcher mode that is determined by CBusy

| CBusy[2]           | CBusy[1:0] | Prefetcher mode                                      |
|--------------------|------------|------------------------------------------------------|
| 1                  | 11         | Disable inaccurate prefetchers                       |
| Can take any value | 10         | Very conservative mode on inaccurate prefetchers     |
| 1                  | 01         | Moderately aggressive mode on inaccurate prefetchers |
| Can take any value | 00         | Fully aggressive mode on inaccurate prefetchers      |
