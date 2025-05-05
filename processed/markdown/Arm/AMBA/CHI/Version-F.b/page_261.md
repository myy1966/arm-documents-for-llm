The rules, in addition to the common rules, to be followed by a Snoopee that receives a SnpUniqueFwd are:

- Snoopee must forward the cache line in Unique state.
- Snoopee that has the cache line in Dirty state must Pass Dirty to the Requester not to Home.
- Snoopee must transition to I state.
- Snoopee must not return data to Home.

RetToSrc bit in the snoop must be set to 0.

Table B4.58 shows the Snoopee cache state transitions and the required Snoop responses.

See Table B4.54 for the symbol key.

Table B4.58: SnpUniqueFwd Snoopee state transitions with Clean and Dirty tags

| Snoopee cache state </br > Initial | Snoopee cache state </br> Final expected | Snoopee cache state </br> Final permitted | RetToSrc | Response to Requester | Response to Home          | TagOp value in response to Home </br> Initial start state of Dirty ᵃ | TagOp value in response to Home </br> Initial start state of Dirty | TagOp value in response to Home </br> Initial start state of Invalid or Clean |
|------------------------------------|------------------------------------------|-------------------------------------------|----------|-----------------------|---------------------------|----------------------------------------------------------------------|--------------------------------------------------------------------|-------------------------------------------------------------------------------|
| I                                  | I                                        | -                                         | 0        | No Fwd                | SnpResp\_I                | -                                                                    | -                                                                  | -                                                                             |
| UC                                 | I                                        | -                                         | 0        | CompData\_UC          | SnpResp\_I\_Fwded\_UC     | -                                                                    | -                                                                  | -                                                                             |
| UCE                                | I                                        | -                                         | 0        | No Fwd                | SnpResp\_I                | -                                                                    | -                                                                  | -                                                                             |
| UD                                 | I                                        | -                                         | 0        | CompData\_UD\_PD      | SnpResp\_I\_Fwded\_UD\_PD | NP ᵇ                                                                 | -                                                                  | -                                                                             |
| UD                                 | I                                        | -                                         | 0        | No Fwd                | SnpRespData\_I\_PD        | P                                                                    | Update                                                             | I, Transfer                                                                   |
| UDP                                | I                                        | -                                         | 0        | No Fwd                | SnpRespDataPtl\_I\_PD     | -                                                                    | -                                                                  | I                                                                             |
| SC                                 | I                                        | -                                         | 0        | CompData\_UC          | SnpResp\_I\_Fwded\_UC     | -                                                                    | -                                                                  | -                                                                             |
| SD                                 | I                                        | -                                         | 0        | CompData\_UD\_PD      | SnpResp\_I\_Fwded\_UD\_PD | NP ᵇ                                                                 | -                                                                  | -                                                                             |
| SD                                 | I                                        | -                                         | 0        | No Fwd                | SnpRespData\_I\_PD        | P                                                                    | Update                                                             | I, Transfer                                                                   |

- ᵃ Indicates if the transition itself is permitted or not. This column is only relevant when the tag initial state is Dirty.
- ᵇ This transition is not permitted because Dirty tags are lost. The Dirty tags are lost because the Snoop response to the Home does not include data with which to pass the Dirty tags to the Home.

#### B4.8.3.5 SnpPreferUnique and SnpPreferUniqueFwd

Use of the SnpPreferUniqueFwd snoop is only permitted if the cache line is cached at a single RN-F.

The rules, in addition to the common rules, to be followed by a Snoopee that receives a SnpPreferUniqueFwd and does not treat SnpPreferUniqueFwd as the Non-forwarding snoop are:

- When the Snoopee is in the process of executing an Exclusive access sequence, using the same address:

    - Snoopee must forward the cache line in SC state.
    - Snoopee must transition to either SD or SC state.
    - Snoopee must not transition to I state, except when in UCE or UDP state.
    - For behavior related to the RetToSrc bit see B4.9 Returning Data with Snoop response related to SnpNotSharedDirtyFwd.
    - A Snoopee that is not in the middle of executing an Exclusive access sequence is permitted, but not expected, to treat the snoop as a Non-invalidating snoop.

- When the Snoopee is not in the process of executing an Exclusive access sequence, using the same address, and treats the snoop as an Invalidating snoop:

    - Snoopee must forward the cache line in Unique state.