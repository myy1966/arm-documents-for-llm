## B4.9 Returning Data with Snoop response

The rules for returning a copy of the cache line with the Snoop response are detailed below.

For Non-forwarding snoops, except SnpMakeInvalid, the rules for returning a copy of the cache line to the Home are:

- Irrespective of the value of RetToSrc, must return a copy if the cache line is Dirty.
- Irrespective of the value of RetToSrc, optionally can return a copy if the cache line is Unique Clean.
- If the RetToSrc value is 1, must return a copy if the cache line is Shared Clean.
- If the RetToSrc value is 0, must not return a copy if the cache line is Shared Clean.

For Forwarding snoops where data is being forwarded, the rules for returning a copy of the cache line to the Home are:

- Irrespective of the value of RetToSrc, must return a copy if a Dirty cache line cannot be forwarded or kept.
- If the RetToSrc value is 1, must return a copy if the cache line is Dirty or Clean.
- If the RetToSrc value is 0, must not return a copy if the cache line is Clean.

RetToSrc is inapplicable and must be set to 0 in:

- SnpCleanShared, SnpCleanInvalid, and SnpMakeInvalid
- SnpOnceFwd and SnpUniqueFwd
- SnpMakeInvalidStash, SnpUniqueStash, SnpStashUnique, and SnpStashShared
- SnpQuery

RetToSrc is applicable and can take any value in all other snoops except SnpDVMOp.

RetToSrc is inapplicable and must be set to 0 in SnpDVMOp.

Home must only set RetToSrc on the Snoop request to a single Request Node.