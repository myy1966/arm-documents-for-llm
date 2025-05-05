Table B4.54: Key to table conventions

| Symbol | Description                     |
|--------|---------------------------------|
| P      | The transition is permitted     |
| NP     | The transition is not permitted |
| -      | TagOp is not applicable         |

- Second column: The response TagOp value when the transition is permitted. The TagOp value in the response:

    - Must be Update if the response state includes Pass Dirty.
    - Must be Transfer if the response does not include Pass Dirty.

**Invalid, Clean** One column:

- TagOp in the response can be:

    - Invalid if the initial tag state is Invalid or Clean.
    - Transfer when the initial tag state is Clean.

In Snoop responses to Home without data, TagOp is inapplicable.

#### B4.8.3.1 SnpOnceFwd

The rules, in addition to the common rules, to be followed by a Snoopee that receives a SnpOnceFwd are:

- Snoopee must forward the cache line in I state.

    - As a consequence, the Snoopee must not forward Pass Dirty to the Requester.

- Snoopee must return data to Home only when Dirty state is changed to Clean or Invalid.
- RetToSrc bit in the snoop must be set to 0.
- Snoopee can ignore the DoNotGoToSD value in the snoop.

Table B4.55 shows the Snoopee cache state transitions and the required Snoop responses.

See Table B4.54 for the symbol key.

Table B4.55: SnpOnceFwd Snoopee state transitions with Clean and Dirty tags

| Snoopee cache state </br > Initial | Snoopee cache state </br> Final expected | Snoopee cache state </br> Final permitted | RetToSrc | Response to Requester | Response to Home      | TagOp value in response to Home </br> Initial start state of Dirty ᵃ | TagOp value in response to Home </br> Initial start state of Dirty | TagOp value in response to Home </br> Initial start state of Invalid or Clean |
|------------------------------------|------------------------------------------|-------------------------------------------|----------|-----------------------|-----------------------|----------------------------------------------------------------------|--------------------------------------------------------------------|-------------------------------------------------------------------------------|
| I                                  | I                                        | -                                         | 0        | No Fwd                | SnpResp\_I            | -                                                                    | -                                                                  | -                                                                             |
| UC                                 | UC                                       | -                                         | 0        | CompData\_I           | SnpResp\_UC\_Fwded\_I | -                                                                    | -                                                                  | -                                                                             |
| UC                                 | SC                                       | I                                         | 0        | CompData\_I           | SnpResp\_SC\_Fwded\_I | -                                                                    | -                                                                  | -                                                                             |
| UC                                 | I                                        | -                                         | 0        | CompData\_I           | SnpResp\_I\_Fwded\_I  | -                                                                    | -                                                                  | -                                                                             |
| UCE                                | UCE                                      | -                                         | 0        | No Fwd                | SnpResp\_UC           | -                                                                    | -                                                                  | -                                                                             |
| UCE                                | I                                        | -                                         | 0        | No Fwd                | SnpResp\_I            | -                                                                    | -                                                                  | -                                                                             |
