Table B4.48 Continued from previous page

| Snoop request type | Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response        |
|--------------------|---------------|----------------------|-----------------------|----------|-----------------------|
| SnpCleanShared     | SD            | SC                   | I                     | 0        | SnpRespData\_SC\_PD   |
| SnpCleanShared     | SD            | I                    | -                     | 0        | SnpRespData\_I\_PD    |
| SnpCleanInvalid    | I             | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanInvalid    | UC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanInvalid    | UCE           | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanInvalid    | UD            | I                    | -                     | 0        | SnpRespData\_I\_PD    |
| SnpCleanInvalid    | UDP           | I                    | -                     | 0        | SnpRespDataPtl\_I\_PD |
| SnpCleanInvalid    | SC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanInvalid    | SD            | I                    | -                     | 0        | SnpRespData\_I\_PD    |
| SnpMakeInvalid     | I             | I                    | -                     | 0        | SnpResp\_I            |
| SnpMakeInvalid     | UC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpMakeInvalid     | UCE           | I                    | -                     | 0        | SnpResp\_I            |
| SnpMakeInvalid     | UD            | I                    | -                     | 0        | SnpResp\_I            |
| SnpMakeInvalid     | UDP           | I                    | -                     | 0        | SnpResp\_I            |
| SnpMakeInvalid     | SC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpMakeInvalid     | SD            | I                    | -                     | 0        | SnpResp\_I            |

#### B4.8.1.5 SnpQuery

Table B4.49 shows the initial, expected final, and other permitted final cache states at the snooped Requester, the RetToSrc field value, and the valid completion response from a snooped RN-F for SnpQuery.

Table B4.49: SnpQuery cache state transitions, RetToSrc value, and valid completion responses

| Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response |
|---------------|----------------------|-----------------------|----------|----------------|
| I             | I                    | -                     | 0        | SnpResp\_I     |
| UC            | UC                   | -                     | 0        | SnpResp\_UC    |
| UCE           | UCE                  | -                     | 0        | SnpResp\_UC    |
| UD            | UD                   | -                     | 0        | SnpResp\_UD    |
| UDP           | UDP                  | -                     | 0        | SnpResp\_UD    |
| SC            | SC                   | -                     | 0        | SnpResp\_SC    |
| SD            | SD                   | -                     | 0        | SnpResp\_SD    |