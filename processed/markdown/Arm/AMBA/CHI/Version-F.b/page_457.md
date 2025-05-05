### B13.10.38 Do not transition to SD state, DoNotGoToSD

This field is an attribute in a Snoop request indicating if a Snoopee is required to not transition to SD state. See B4.10 Do not transition to SD.

Applicable, and can take any value in:

- SnpOnce, SnpOnceFwd
- SnpClean, SnpCleanFwd
- SnpNotSharedDirty, SnpNotSharedDirtyFwd
- SnpShared, SnpSharedFwd
- SnpPreferUnique, SnpPreferUniqueFwd

Applicable, and must be set to 1 in:

- SnpStashShared, SnpStashUnique
- SnpUnique, SnpUniqueFwd. SnpUniqueStash
- SnpCleanShared
- SnpCleanInvalid
- SnpMakeInvalid, SnpMakeInvalidStash

Inapplicable, and must be set to 0 in:

- SnpQuery
- SnpDVMOp

Table B13.29 shows the DoNotGoToSD value encodings.

Table B13.29: DoNotGoToSD value encodings

| DoNotGoToSD | Description                                                                                                                            |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------|
| 0           | Permitted to transition to SD state.                                                                                                   |
| 1           | Transitioning to SD state is not permitted. If already in SD state, must exit SD state in response to the snoop, except for SnpStash*. |

### B13.10.39 Protocol Credit Type, PCrdType

This field indicates the type of credit being granted or returned. See Table B13.30.

Table B13.30 shows the PCrdType value encodings.

Table B13.30: PCrdType value encodings

| PCrdType | PCrdType | PCrdType                           | Description                        |
|----------|----------|------------------------------------|------------------------------------|
| 0x0      | 0xF      | P-Credit type 0 to 15 respectively | P-Credit type 0 to 15 respectively |

### B13.10.40 Tag Operation, TagOp

This field indicates the operation to be performed on the tags present in the corresponding DAT channel.