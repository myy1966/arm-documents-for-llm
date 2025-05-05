Table B4.45 Continued from previous page

| Initial state | Final expected state | Final permitted state | RetToSrc ᵃ | Snoop response        |
|---------------|----------------------|-----------------------|------------|-----------------------|
| UD            | UD                   | SD                    | X          | SnpRespData\_UD       |
| UD            | SD                   | -                     | X          | SnpRespData\_SD       |
| UD            | SC                   | I                     | X          | SnpRespData\_SC\_PD   |
| UD            | I                    | -                     | X          | SnpRespData\_I\_PD    |
| UDP           | I                    | -                     | X          | SnpRespDataPtl\_I\_PD |
| UDP           | UDP                  | -                     | X          | SnpRespDataPtl\_UD    |
| SC            | SC                   | I                     | 0          | SnpResp\_SC           |
| SC            | SC                   | I                     | 1          | SnpRespData\_SC       |
| SC            | I                    | -                     | 0          | SnpResp\_I            |
| SC            | I                    | -                     | 1          | SnpRespData\_I        |
| SD            | SD                   | -                     | X          | SnpRespData\_SD       |
| SD            | SC                   | I                     | X          | SnpRespData\_SC\_PD   |
| SD            | I                    | -                     | X          | SnpRespData\_I\_PD    |

- ᵃ X indicates that the protocol requirements apply for both states of RetToSrc.

#### B4.8.1.2 SnpClean, SnpShared, SnpNotSharedDirty, and SnpPreferUnique

Table B4.46 shows the initial, expected final, and other permitted final cache states at the snooped Requester, the RetToSrc field value, and the valid completion response from a snooped RN-F for SnpClean, SnpShared, SnpNotSharedDirty and SnpPreferUnique. Table B4.46 must be used to determine SnpPreferUnique cache state transitions when the Snoopee is in the middle of executing an Exclusive access sequence. A Snoopee that is not in the middle of executing an Exclusive access is permitted, but not expected, to use Table B4.46 to determine SnpPreferUnique cache state transitions.

SnpPreferUnique is applicable when the Snoopee is in the middle of executing an Exclusive sequence. SnpPreferUnique is protocol compliant at any time. See also Table B4.47.

See B4.8.3.5 SnpPreferUnique and SnpPreferUniqueFwd for constraints on determining when a Requester is in the middle of executing an exclusive sequence.