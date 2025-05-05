A DataPull request in a Snoop response to SnpStashUnique must be treated as a ReadUnique request. A DataPull request in a Snoop response to SnpStashShared must be treated as a ReadNotSharedDirty request.

The inclusion of DataPull in the Snoop response must ensure that the initial state must not violate the initial state conditions permitted for the corresponding independent Read requests. See B4.2.1 Read transactions.

Table B4.51 shows the Snoopee cache state transitions, the required Snoop responses, and DataPull options for SnpStashUnique.

Table B4.51: Snoop response to SnpStashUnique

| Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response    |
|---------------|----------------------|-----------------------|----------|-------------------|
| I             | I                    | -                     | 0        | SnpResp\_I        |
| I             | I                    | -                     | 0        | SnpResp\_I\_Read  |
| UC            | UC                   | -                     | 0        | SnpResp\_UC       |
| UC            | UC                   | -                     | 0        | SnpResp\_I        |
| UCE           | UCE                  | -                     | 0        | SnpResp\_UC       |
| UCE           | UCE                  | -                     | 0        | SnpResp\_UC\_Read |
| UCE           | UCE                  | -                     | 0        | SnpResp\_I        |
| UD            | UD                   | -                     | 0        | SnpResp\_UD       |
| UD            | UD                   | -                     | 0        | SnpResp\_I        |
| UDP           | UDP                  | -                     | 0        | SnpResp\_UD       |
| UDP           | UDP                  | -                     | 0        | SnpResp\_I        |
| SC            | SC                   | -                     | 0        | SnpResp\_SC       |
| SC            | SC                   | -                     | 0        | SnpResp\_SC\_Read |
| SC            | SC                   | -                     | 0        | SnpResp\_I        |
| SD            | SD                   | -                     | 0        | SnpResp\_SD       |
| SD            | SD                   | -                     | 0        | SnpResp\_SD\_Read |
| SD            | SD                   | -                     | 0        | SnpResp\_I        |

Table B4.52 shows the Snoopee cache state transitions, the required Snoop responses, and Data Pull options for SnpStashShared.

Table B4.52: Snoop response to SnpStashShared

| Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response              |
|---------------|----------------------|-----------------------|----------|-----------------------------|
| I             | I                    | -                     | 0        | SnpResp\_I\_Read SnpResp\_I |
| UC            | UC                   | -                     | 0        | SnpResp\_UC SnpResp\_I      |

Continued on next page