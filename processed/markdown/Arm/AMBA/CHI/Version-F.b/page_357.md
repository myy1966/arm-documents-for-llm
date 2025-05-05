Table B9.3 – Continued from previous page

| Read transaction                                           | Associated Data-only and Non-data packets </br> DataSepResp </br> OK | Associated Data-only and Non-data packets </br> DataSepResp </br> EXOK | Associated Data-only and Non-data packets </br> DataSepResp </br> DERR | Associated Data-only and Non-data packets </br> DataSepResp </br> NDERR | Associated Data-only and Non-data packets </br> RespSepData </br> OK | Associated Data-only and Non-data packets </br> RespSepData </br> EXOK | Associated Data-only and Non-data packets </br> RespSepData </br> DERR | Associated Data-only and Non-data packets </br> RespSepData </br> NDERR |
|------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|
| ReadClean </br> ReadNotSharedDirty </br> ReadShared        | Y                                                                    | N                                                                      | Y                                                                      | Y                                                                       | Y                                                                    | N                                                                      | N                                                                      | Y                                                                       |
| ReadUnique </br> ReadPreferUnique ᵃ </br> MakeReadUnique ᵇ | Y                                                                    | N                                                                      | Y                                                                      | Y                                                                       | Y                                                                    | N                                                                      | N                                                                      | Y                                                                       |

- ᵃ A response of OK in the returned data response is not be taken as a failure of ReadPreferUnique.

    Failure of the exclusive sequence is only determined from the corresponding MakeReadUnique Excl or CleanUnique Excl transaction completion.

- ᵇ Applicable only when data is returned to the Requester. See Table B9.4 for permitted errors when data is not returned to the Requester.

Table B9.4 shows the legal combincations of RespSepData and DataSepResp in relation to their message origins.

Table B9.4: Legal combinations of RespSepData and DataSepResp according to message origins

| RespSepData | DataSepResp | Legal combination when DataSepResp </br> From Home | Legal combination when DataSepResp </br> From Subordinate |
|-------------|-------------|----------------------------------------------------|-----------------------------------------------------------|
| OK          | OK          | Y                                                  | Y                                                         |
| OK          | NDERR       | Y                                                  | Y                                                         |
| OK          | DERR        | Y                                                  | Y                                                         |
| NDERR       | NDERR       | Y                                                  | -                                                         |

#### B9.1.4.2 Dataless transactions

A DERR can be reported for a Dataless transaction when the processing of the transaction by another component encounters a data corruption error. This DERR can be indicated back to the originating component, even though a transfer of data does not occur.

Table B9.5 shows the Dataless transaction packets legal RespErr field values.