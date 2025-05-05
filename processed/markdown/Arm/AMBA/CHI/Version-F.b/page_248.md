## B4.8 Cache state transitions at a Snoopee

This section specifies the cache state transitions and completion responses for the following Snoop transactions:

- B4.8.1 Non-Forwarding and Non-stash Snoop transactions
- B4.8.2 Stash Snoop transactions
- B4.8.3 Forwarding Snoop transactions

A Snoopee, an RN-F that receives a snoop, performs two actions. One action is a state change of the cached line and the second action is sending a response message either to the Home, or to both the Home and the Requester.

The cache state change depends on the snoop type, the initial state of the cache line and the value of DoNotGoToSD in the snoop. See B4.10 Do not transition to SD.

The Snoopee must send a response to Home either with Data or without Data. In addition, for Forwarding snoops the Snoopee can also forward a Data response to the Requester.

The type of response sent is determined by the snoop type, initial cache state, cache state change, and the value of RetToSrc. See B4.9 Returning Data with Snoop response.

### B4.8.1 Non-Forwarding and Non-stash Snoop transactions

The Non-forwarding and Non-stash Snoop transactions are:

- B4.8.1.1 SnpOnce
- B4.8.1.2 SnpClean, SnpShared, SnpNotSharedDirty, and SnpPreferUnique
- B4.8.1.3 SnpUnique and SnpPreferUnique
- B4.8.1.4 SnpCleanShared, SnpCleanInvalid, and SnpMakeInvalid
- B4.8.1.5 SnpQuery

#### B4.8.1.1 SnpOnce

Table B4.45 shows for SnpOnce, the initial, expected final, and other permitted final cache states at the snooped Requester, the RetToSrc field value, and the valid completion response from a snooped RN-F for SnpOnce.

Table B4.45: SnpOnce Cache state transitions, RetToSrc value, and valid completion responses

| Initial state | Final expected state | Final permitted state | RetToSrc ᵃ | Snoop response  |
|---------------|----------------------|-----------------------|------------|-----------------|
| I             | I                    | -                     | X          | SnpResp\_I      |
| UC            | UC                   | I, SC                 | X          | SnpResp\_UC     |
| UC            | UC                   | I, SC                 | X          | SnpRespData\_UC |
| UC            | SC                   | I                     | X          | SnpResp\_SC     |
| UC            | SC                   | I                     | X          | SnpRespData\_SC |
| UC            | I                    | -                     | X          | SnpResp\_I      |
| UC            | I                    | -                     | X          | SnpRespData\_I  |
| UCE           | UCE                  | I                     | X          | SnpResp\_UC     |
| UCE           | I                    | -                     | X          | SnpResp\_I      |

Continued on next page