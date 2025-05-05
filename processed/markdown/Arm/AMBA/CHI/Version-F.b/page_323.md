## B7.5 Stash messages

Stash messages are classified as:

- Write requests:

    - WriteUniqueFullStash
    - WriteUniquePtlStash

See B4.2.3 Write transactions.

- Dataless requests:

    - StashOnceUnique
    - StashOnceSepUnique
    - StashOnceShared
    - StashOnceSepShared

See B4.2.2 Dataless transactions.

- Snoop requests:

    - SnpUniqueStash
    - SnpMakeInvalidStash
    - SnpStashUnique
    - SnpStashShared

See B4.3 Snoop request types.

- Stash responses:

    - Comp
    - StashDone
    - CompStashDone

See B2.3.4 Stash transactions.

### B7.5.1 Supporting REQ packet fields

The fields defined in the REQ packet to support Stash requests are:

- StashNID, StashLPID
- StashNIDValid, StashLPIDValid

Table B7.3 shows the valid StashNIDValid and StashLPIDValid encodings.

## Table B7.3: Valid StashNIDValid and StashLPIDValid encodings

| StashNIDValid | StashLPIDValid | Comments                                        |
|---------------|----------------|-------------------------------------------------|
| 0             | 0              | Stash target is not specified                   |
| 0             | 1              | Reserved                                        |
| 1             | 0              | Only a target Request Node is specified         |
| 1             | 1              | Both target Request Node and LPID are specified |

See B13.10 Protocol flit fields.