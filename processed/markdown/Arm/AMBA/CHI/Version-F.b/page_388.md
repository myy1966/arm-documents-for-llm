- Back invalidation from the snoop filter resulting in snoop response with data must obtain PBHA value along with data from the Snoopee. Alternatively, the snoop filter can hold PBHA values and add them to the data received in the snoop response.

> **_NOTE:_** A non-exhaustive list of how PBHA values can become imprecise include:
>
> - Address translation is not used by the requests.
> - PBHA value is not held in the caches.
> - PBHA value is not provided alongside stashing transactions.
> - Multiple Virtual Addresses mapped to the same PA where translations provide different PBHA values.
> - Appropriate Cache Maintenance Operations have not been performed after the modification of the PBHA value.