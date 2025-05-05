Table B4.17 – Continued from previous page

| Request              | Initial state </br> UD | Initial state </br> UC | Initial state </br> SD | Initial state </br> SC | Initial state </br> I | Initial state </br> UDP | Initial state </br> UCE |
|----------------------|------------------------|------------------------|------------------------|------------------------|-----------------------|-------------------------|-------------------------|
| Request              | UD                     | UC                     | SD                     | SC                     | I                     | UDP                     | UCE                     |
| WriteUniquePtl       | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteUniqueFull      | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteUniqueZero      | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteUniquePtlStash  | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteUniqueFullStash | -                      | -                      | -                      | -                      | Y                     | -                       | -                       |
| WriteBackPtl         | -                      | -                      | -                      | -                      | -                     | Y                       | -                       |
| WriteBackFull        | Y                      | -                      | Y                      | -                      | -                     | -                       | -                       |
| WriteCleanFull       | Y                      | -                      | Y                      | -                      | -                     | -                       | -                       |
| WriteEvictFull       | -                      | Y                      | -                      | -                      | -                     | -                       | -                       |
| WriteEvictOrEvict    | -                      | Y                      | -                      | Y                      | -                     | -                       | -                       |

#### B4.2.3.5 Final cache state at the Requester

The permitted Requester cache state at the completion of a Write transaction, except for WriteCleanFull, is Invalid.

The permitted Requester cache state at the completion of a WriteCleanFull transaction is UC or SC.

#### B4.2.3.6 Peer cache state

The Peer Request Node cache state at the completion of WriteNoSnpPtl, WriteNoSnpFull, WriteNoSnpDef, and WriteNoSnpZero is not applicable.

The Peer Request Node cache state at the completion of WriteUniquePtl, WriteUniqueFull, WriteUniqueZero, WriteUniquePtlStash, and WriteUniqueFullStash must be Invalid.

The Peer Request Node cache state at the completion of CopyBack requests is not changed. The Home Node is not required to snoop the Peer Request Nodes to change their cache state.

#### B4.2.4 Combined Write requests

Write transactions can be combined with Cache Maintenance transactions when both are to the same address. The ability to combine the two requests to the same address is useful when a CMO or PCMO transaction reaches a point in the system where a Write operation must be completed before the CMO or PCMO transaction can be initiated. The use of a single Combined Write transaction avoids the need to serialize the Write and CMO or PCMO transactions. The point where the two requests are combined can be a Request Node or Home Node.

Table B4.18 and Table B4.19 show the Write, CMO, and PCMO combinations for which combining is permitted. Empty table cells indicate a combination that is not permitted or not applicable.

> **_NOTE:_** Deep is an attribute on Persistent CMO requests. Deep has not been listed explicitly as a CMO type in Table B4.18 and Table B4.19.
>
> When a PCMO is combined with a write, the PCMO is treated as a CleanSharedPersistSep, that is, in