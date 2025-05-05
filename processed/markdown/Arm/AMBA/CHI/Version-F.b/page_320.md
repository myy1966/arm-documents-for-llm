## B7.3 Independent Stash request

The second mechanism for implementing cache stashing is to permit the Stash request to be sent separated in time from the writing of Stash data. Examples of when such a mechanism is useful are:

- When the data that is being written is not required by the target immediately. This delayed Stash avoids polluting the cache with data that is not used immediately.
- When the data is already in the system and the data has to be prefetched into caches.
- When the process using the data being written is not scheduled when the data is written, and therefore the precise target of the Stash data is not known until later.

In these cases, a Requester can use StashOnce or StashOnceSep requests to request Home or a peer node to fetch a cache line.

The rules for sending and processing an independent Stash request at the Stash requester, Home, and the Stash target are as follows:

Requester Node responsibilities:

- Sends StashOnceUnique or StashOnceSepUnique to Home if the stashed cache line is to be modified.
- Sends StashOnceShared or StashOnceSepShared to Home if the stashed cache line is not to be modified.
- Sends StashOnceSep only if the Requester is capable of handling the StashDone response.
- The StashOnce and StashOnceSep requests provide a Stash target when the data is to be stashed in a peer cache.
- The StashOnce and StashOnceSep requests do not provide a Stash target when the data is to be allocated in the next level cache.
- The Requester, upon receiving the Comp response, is permitted to release some request resources, while keeping track of the number of outstanding StashDone responses. This count of the number of outstanding StashDone responses can be done per Stash group, using the Requester defined Stash Group ID, specified by the StashGroupID field value.

Home Node responsibilities:

- Permitted to send a RetryAck response to a Stash request and follow the Retry transaction flow.
- Send a SnpStashUnique to the target RN-F for StashOnceUnique and StashOnceSepUnique.
- Send a SnpStashShared to the target RN-F for StashOnceShared and StashOnceSepShared.
- Permitted to not send a Snoop request in response to a Stash request.
- Must send a Comp response, even if the Stash request is abandoned.
- For the StashOnce, the Home must send a Comp only after establishing processing order for the received request that is guaranteeing that any request to the same address received later from any Requester is ordered behind this request. The Comp response must come from the PoC.
- For the StashOnceSep request, the Home must send a Comp only after establishing the guarantee that a RetryAck response will not be sent. The StashDone response must only be sent after establishing the guarantee that the request is ordered at the Home.
- Fetches the addressed cache line from memory into the shared system cache when a Stash request without a Stash target is received.
- Permitted to send Comp after receiving the Stash request, and before sending any SnpStash* or receiving the Snoop response.
- Send Comp with a Non-Invalid state, if the cache line is cached in the cache at the next level.