## C2.4 Data communicating nodes

Table C2.4 shows the Data communicating nodes.

For some Data, both an expected target and a permitted target are given. The use of the permitted target can occur in the case of an incorrect address decode. The permitted target must complete the transaction in a protocol compliant manner. In Table C2.4, unless explicitly stated otherwise, a reference to a Write transaction includes both the individual Write transaction and the corresponding Combined Write transaction.

Table C2.4: Data communicating nodes

<!-- MERGE table -->

| Data       |                      | From             | To Expected                 | Permitted |
|------------|----------------------|------------------|-----------------------------|-----------|
| Upstream   | CompData             | ICN(HN-F, HN-I)  | RN-F, RN-D, RN-I            | -         |
|            |                      | SN-F             | RN-F, RN-D, RN-I, ICN(HN-F) | -         |
|            |                      | SN-I             | RN-F, RN-D, RN-I, ICN(HN-I) | -         |
|            | DataSepResp          | ICN(HN-F, HN-I)  | RN-F, RN-D, RN-I            | -         |
|            |                      | SN-F             | RN-F, RN-D, RN-I            | ICN(HN-F) |
|            |                      | SN-I             | RN-F, RN-D, RN-I            | ICN(HN-I) |
| Downstream | CopyBackWriteData    | RN-F             | ICN(HN-F)                   | ICN(HN-I) |
|            | WriteDataCancel      | RN-F, RN-D, RN-I | ICN(HN-F, HN-I), SN-F, SN-I | -         |
|            |                      | ICN(HN-F)        | SN-F                        | -         |
|            |                      | ICN(HN-I)        | SN-I                        | -         |
|            | NonCopyBackWriteData | RN-F, RN-D, RN-I | ICN(HN-F, HN-I), SN-F, SN-I | -         |
|            |                      | RN-F, RN-D       | ICN(MN)                     | -         |
|            |                      | ICN(HN-F)        | SN-F                        | -         |
|            |                      | ICN(HN-I)        | SN-I                        | -         |
|            | NCBWrDataCompAck     | RN-F, RN-D, RN-I | ICN(HN-F, HN-I)             | -         |
|            | SnpRespData          | RN-F             | ICN(HN-F)                   |           |
|            | SnpRespDataFwded     |                  |                             |           |
|            | SnpRespDataPtl       |                  |                             |           |
|            | CompData             | RN-F             | RN-F, RN-D, RN-I            | -         |