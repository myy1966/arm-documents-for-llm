## B7.2 Write with Stash hint

The rules for sending and processing a WriteUniqueFullStash and WriteUniquePtlStash request at the Stash requester, the Home, and the Stash target node are as follows:

Requester responsibilities:

- Sends a WriteUniqueFullStash or WriteUniquePtlStash request depending on whether a full cache line or a partial cache line is to be written.
- The request is expected to include a Stash target.

Home responsibilities:

- Permitted to send a RetryAck response to a WriteUniqueStash request and follow the Retry transaction flow.
- Sends SnpUniqueStash to the identified Stash target.
- Sends SnpUnique to all other Requesters that share the cache line.
- Permitted to send SnpMakeInvalidStash and SnpMakeInvalid instead of SnpUniqueStash and SnpUnique respectively for WriteUniqueFullStash.
- Send Comp to the Requester after the coherency action is completed.
- Permitted to ignore the stash hint in the Write request and process the request as a regular WriteUnique.
- Handles a request without a Stash target in the manner described in B7.4.2 Stash target not specified.
- Permitted to use DMT to get data from SN-F to the Stash target in response to a DataPull request, when the data is neither available at Home nor obtained from any caches.
- Permitted to use separate Non-data and Data-only response to the Stash target in response to a DataPull request.

The Stash target responsibilities:

- The responses that include Data Pull are:

    - SnpResp\_I\_Read
    - SnpRespData\_I\_Read
    - SnpRespData\_I\_PD\_Read
    - SnpRespDataPtl\_I\_PD\_Read

- Must not request Data Pull if:

    - Snoop has an address hazard with an outstanding request.
    - The Stash target has an outstanding request to the same address that has received a DBIDRespOrd but has not completed.

- When requesting Data Pull:

    - The Stash target must guarantee the Read data is accepted without any structural or protocol dependencies that could result in deadlock.
    - The Read request is treated by Home as ReadUnique.
    - The Stash target must populate the DBID field in the response with the TxnID that is to be used by Home for the Read transaction. If the Snoop response with DataPull includes data, the DBID field value in all data packets must be the same.

- Permitted to ignore the Stash hint and handle the snoop as SnpUnique.