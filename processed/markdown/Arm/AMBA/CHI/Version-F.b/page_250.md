Table B4.46: SnpClean, SnpShared, SnpNotSharedDirty and SnpPreferUnique cache state transitions, RetToSrc value, and valid completion responses

| Initial state | Final expected state | Final permitted state | RetToSrc ᵃ | Snoop response      |
|---------------|----------------------|-----------------------|------------|---------------------|
| I             | I                    | -                     | X          | SnpResp\_I          |
| UC            | SC                   | I                     | X          | SnpResp\_SC         |
| UC            | SC                   | I                     | X          | SnpRespData\_SC     |
| UC            | I                    | -                     | X          | SnpResp\_I          |
| UC            | I                    | -                     | X          | SnpRespData\_I      |
| UCE           | I                    | -                     | X          | SnpResp\_I          |
| UD            | SD ᵇ                 | -                     | X          | SnpRespData\_SD     |
| UD            | SC                   | I                     | X          | SnpRespData\_SC\_PD |
| UD            | I                    | -                     | X          | SnpRespData\_I\_PD  |
| UDP           | I                    | -                     | X          | SnpRespDataPtl_I_PD |
| SC            | SC                   | I                     | 0          | SnpResp\_SC         |
| SC            | SC                   | I                     | 1          | SnpRespData\_SC     |
| SC            | I                    | -                     | 0          | SnpResp\_I          |
| SC            | I                    | -                     | 1          | SnpRespData\_I      |
| SD            | SD ᵇ                 | -                     | X          | SnpRespData\_SD     |
| SD            | SC                   | I                     | X          | SnpRespData\_SC\_PD |
| SD            | I                    | -                     | X          | SnpRespData\_I\_PD  |

- ᵃ X indicates that the protocol requirements apply for both states of RetToSrc.
- ᵇ This state transition is not permitted if DoNotGoToSD is set.

#### B4.8.1.3 SnpUnique and SnpPreferUnique

Table B4.47 shows the initial, expected final, and other permitted final cache states at the snooped Requester, the RetToSrc field value, and the valid completion response from a snooped RN-F for SnpUnique, for SnpUnique and SnpUniquePrefer. Table B4.47 is expected to be used to determine SnpPreferUnique cache state transitions when the Snoopee is not in the middle of executing an Exclusive access sequence.

SnpPreferUnique is only applicable when the Snoopee is not executing an Exclusive sequence.