## B7.1 Overview

Cache stashing is a mechanism to install data within particular caches in a system. Cache stashing ensures that data is located close to its point of use, improving the system performance.

Cache stashing is permitted to Snoopable memory only.

The CHI protocol supports two main forms of cache stashing transaction:

**WriteUniqueStash** Write with stash hint. This is used when the cache in which the data should be allocated is known at the point in time that the data is written. A write with stash hint can be a [Full] or [Ptl] cache line write, and this affects the Snoop transactions that are used. See B7.2 Write with Stash hint.

**StashOnce** Independent stash request. This is used when the request to stash data into a particular cache is separated from the writing of the data. An independent Stash transaction can indicate if the cache line should be held in a Unique or Shared state by using a StashOnceUnique or StashOnceSepUnique, or a StashOnceShared or StashOnceSepShared transaction respectively, which corresponds to whether the next expected use of the cache line is for storing or for reading. See B7.3 Independent Stash request.

Both forms of cache stashing can target installation of data at different cache levels. The Stash target cache can be a peer cache, specified by using the peer cache target NodeID, or an LP cache within the peer node, if the peer node has multiple logical processors. The LP is identified by the LPID in the target cache field. See B7.4 Stash target identifiers.

The Cache stashing requests can also target the cache below the peer cache in the cache hierarchy, which can be an interconnect cache or a system cache. This is done by not specifying the peer cache NodeID. See B7.4.2 Stash target not specified.

In all cases of cache stashing, the Stashing is only a performance hint and it is permitted for the Stash request receiver to not perform the stashing behavior.

### B7.1.1 Snoop requests and Data Pull

The following Snoop requests are used to notify a Stash target:

- SnpUniqueStash
- SnpMakeInvalidStash
- SnpStashUnique
- SnpStashShared

Table B7.1 shows the Snoop requests associated with each of the Stash requests.

Table B7.1: Stash request and the corresponding Snoop request

| Stash request        | Snoop request                           |
|----------------------|-----------------------------------------|
| WriteUniquePtlStash  | SnpUniqueStash or SnpMakeInvalidStash ᵃ |
| WriteUniqueFullStash | SnpMakeInvalidStash                     |
| StashOnceUnique      | SnpStashUnique                          |
| StashOnceSepUnique   | SnpStashUnique                          |

Continued on next page