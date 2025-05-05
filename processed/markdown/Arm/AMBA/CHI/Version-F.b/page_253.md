### B4.8.2 Stash Snoop transactions

The following sub-sections show the permitted responses for the Stash type snoops:

- B4.8.2.1 SnpUniqueStash and SnpMakeInvalidStash
- B4.8.2.2 SnpStashUnique and SnpStashShared

#### B4.8.2.1 SnpUniqueStash and SnpMakeInvalidStash

The permitted responses to SnpUniqueStash and SnpMakeInvalidStash are the same as the responses to SnpUnique and SnpMakeInvalid respectively.

The RetToSrc bit value must not be set to 1 in SnpUniqueStash and SnpMakeInvalidStash.

Any Snoop response to SnpUniqueStash and SnpMakeInvalidStash can include a DataPull request. A DataPull request in a Snoop response to SnpUniqueStash and SnpMakeInvalidStash must be treated as a ReadUnique request.

Table B4.50 shows the Snoopee cache state transitions and required Snoop responses for SnpUniqueStash and SnpMakeInvalidStash. The Snoop responses do not include the DataPull options. DataPull is permitted with any Snoop response.

Table B4.50: Snoop response to SnpUniqueStash and SnpMakeInvalidStash

| Snoop request type  | Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response        |
|---------------------|---------------|----------------------|-----------------------|----------|-----------------------|
| SnpUniqueStash      | I             | I                    | -                     | 0        | SnpResp\_I            |
| SnpUniqueStash      | UC            | I                    | -                     | 0        | SnpRespData\_I        |
| SnpUniqueStash      | UC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpUniqueStash      | UCE           | I                    | -                     | 0        | SnpResp\_I            |
| SnpUniqueStash      | UD            | I                    | -                     | 0        | SnpRespData\_I\_PD    |
| SnpUniqueStash      | UDP           | I                    | -                     | 0        | SnpRespDataPtl\_I\_PD |
| SnpUniqueStash      | SC            | I                    | -                     | 0        | SnpResp\_I            |
| SnpUniqueStash      | SD            | I                    | -                     | 0        | SnpResp\_I\_PD        |
| SnpMakeInvalidStash | Any           | I                    | -                     | 0        | SnpResp\_I            |

#### B4.8.2.2 SnpStashUnique and SnpStashShared

For SnpStashUnique and SnpStashShared, the Snoopee must not change cache state.

The Snoopee is permitted to not perform a cache lookup before responding, in which case the Snoop response must be SnpResp\_I.

The Snoopee is permitted to include the precise cache state in the response.

A Snoop response can include DataPull only if the cache state in the response is precise.

The Snoopee can include a DataPull in response to a SnpStashUnique only if the cache-data is not present, or present in a Shared state. The Snoopee can include Data Pull in response to SnpStashShared only if the cache cache-data is not present.