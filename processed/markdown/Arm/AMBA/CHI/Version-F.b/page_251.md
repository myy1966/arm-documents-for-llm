Table B4.47: SnpUnique and SnpUniquePrefer cache state transitions, RetToSrc value, and valid completion responses

| Initial state | Final expected state | Final permitted state | RetToSrc ᵃ | Snoop response        |
|---------------|----------------------|-----------------------|------------|-----------------------|
| I             | I                    | -                     | X          | SnpResp\_I            |
| UC            | I                    | -                     | X          | SnpResp\_I            |
| UC            | I                    | -                     | X          | SnpRespData\_I        |
| UCE           | I                    | -                     | X          | SnpResp\_I            |
| UD            | I                    | -                     | X          | SnpRespData\_I\_PD    |
| UDP           | I                    | -                     | X          | SnpRespDataPtl\_I\_PD |
| SC            | I                    | -                     | 0          | SnpResp\_I            |
| SC            | I                    | -                     | 1          | SnpRespData\_I        |
| SD            | I                    | -                     | X          | SnpRespData\_I\_PD    |

- ᵃ X indicates that the protocol requirements apply for both states of RetToSrc.

#### B4.8.1.4 SnpCleanShared, SnpCleanInvalid, and SnpMakeInvalid

Table B4.48 shows the initial, expected final, and other permitted final cache states at the snooped Requester, the RetToSrc field value, and the valid completion response from a snooped RN-F for SnpCleanShared, SnpCleanInvalid, and SnpMakeInvalid.

Table B4.48: Cache state transitions, RetToSrc value, and valid completion responses

| Snoop request type | Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response        |
|--------------------|---------------|----------------------|-----------------------|----------|-----------------------|
| SnpCleanShared     | I             | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanShared     | UC            | UC                   | I, SC                 | 0        | SnpResp\_UC           |
| SnpCleanShared     | UC            | SC                   | I                     | 0        | SnpResp\_SC           |
| SnpCleanShared     | UC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanShared     | UCE           | I                    | -                     | 0        | SnpResp\_I            |
| SnpCleanShared     | UD            | UC                   | I, SC                 | 0        | SnpRespData\_UC\_PD   |
| SnpCleanShared     | UD            | SC                   | I                     | 0        | SnpRespData\_SC\_PD   |
| SnpCleanShared     | UD            | I                    | -                     | 0        | SnpRespData\_I\_PD    |
| SnpCleanShared     | UDP           | I                    | -                     | 0        | SnpRespDataPtl\_I\_PD |
| SnpCleanShared     | SC            | SC                   | I                     | 0        | SnpResp\_SC           |
| SnpCleanShared     | SC            | I                    | -                     | 0        | SnpResp\_I            |

Continued on next page