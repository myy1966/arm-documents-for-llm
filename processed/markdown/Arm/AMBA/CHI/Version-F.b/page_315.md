Multiple Exclusive transactions to Non-snoopable memory locations, either read or write, to the same or different addresses, from the same LP must not be outstanding at the same time.

If the Subordinate Node does not support Exclusive accesses, as indicated by an Exclusive Fail on the Exclusive ReadNoSnp, the write updates the location if the write is given an Exclusive Fail response.

If the Subordinate Node does support Exclusive accesses, as indicated by an Exclusive Pass on the Exclusive ReadNoSnp, the write does not update the location if the write is given an Exclusive Fail response.