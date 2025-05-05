## B6.3 Exclusive transactions

The following transaction types support Exclusive accesses through an Excl bit:

- Exclusive Load transaction to a Snoopable location:

    - ReadClean
    - ReadNotSharedDirty
    - ReadShared
    - ReadPreferUnique

- Exclusive Store transaction to a Snoopable location:

    - CleanUnique
    - MakeReadUnique

- Exclusive Load transaction to a Non-snoopable location:

    - ReadNoSnp

- Exclusive Store transaction to a Non-snoopable location:

    - WriteNoSnp

The communicating node pairs are:

- For Exclusives to a Snoopable location:

    - RN-F to ICN(HN-F)

- For Exclusives to a Non-snoopable location:

    - RN-F, RN-D, RN-I to ICN(HN-F, HN-I)
    - ICN(HN-F) to SN-F
    - ICN(HN-I) to SN-I

An exclusive transaction must use the correct LPID value, see B2.4.7 Logical Processor Identifier, LPID.

### B6.3.1 Responses to Exclusive requests

Transaction responses to Exclusive requests are similar to the normal responses to reads and writes with the following exceptions:

- ReadClean, ReadNotSharedDirty, and ReadShared Exclusive transactions:

    - Must not use separate Comp and data response.
    - Requests that do not fail must not use either DMT or DCT.

- ReadNoSnp Exclusive transactions that do not fail, must not use DMT.
- WriteNoSnpFull and WriteNoSnpPtl transactions, must not use DWT if the Exclusive monitor is located at the Home and the Exclusive check fails.

However, the response for the following Exclusive transactions must also indicate if the exclusive request has passed or failed:

- ReadClean
- ReadNotSharedDirty
- ReadShared
- ReadNoSnp
- CleanUnique
- WriteNoSnpFull
- WriteNoSnpPtl