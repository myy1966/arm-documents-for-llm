Table B4.52 Continued from previous page

| Initial state | Final expected state | Final permitted state | RetToSrc | Snoop response                           |
|---------------|----------------------|-----------------------|----------|------------------------------------------|
| UCE           | UCE                  | -                     | 0        | SnpResp\_UC SnpResp\_UC\_Read SnpResp\_I |
| UD            | UD                   | -                     | 0        | SnpResp\_UD                              |
| UDP           | UDP                  | -                     | 0        | SnpResp\_UD SnpResp\_I                   |
| SC            | SC                   | -                     | 0        | SnpResp\_SC SnpResp\_I                   |
| SD            | SD                   | -                     | 0        | SnpResp\_SD SnpResp\_I                   |

### B4.8.3 Forwarding Snoop transactions

Forwarding (Fwd) type snoops are used by Home to support DCT. The Forwarding Snoop transactions are:

- B4.8.3.1 SnpOnceFwd
- B4.8.3.2 SnpCleanFwd, SnpNotSharedDirtyFwd
- B4.8.3.3 SnpSharedFwd
- B4.8.3.4 SnpUniqueFwd
- B4.8.3.5 SnpPreferUnique and SnpPreferUniqueFwd

The rules, common to all Forwarding snoops at the Snoopee are:

- Expected, but not required, to forward a copy of the cache line to the Requester if the cache line is in one of the following states:

    - UD
    - UC
    - SD
    - SC

- Not permitted to set the FwdNID to the same node ID as the Snoopee. That is, forwarded data cannot be requested from a Snoopee to itself.
- The Snoopee is permitted, but not expected, to convert the Snoop to its corresponding Non-forwarding type.
- Must not forward data in Unique state in response to a Non-invalidating type snoop.
- Snoopee receiving a Snoop request with the DoNotGoToSD bit set, except when the Snoop is SnpOnceFwd, must not transition to SD, even if the coherency conditions permit it.
- In certain cases, based on the Snoop type, the state of the cache line at the Snoopee, and the RetToSrc value in the Snoop request, the Snoopee forwards a copy to Home along with a copy to the Requester. Forwarding snoops must not be used if the original request requests tags. If tags are available, Clean tags are permitted to be forwarded to the Requester along with the data.
- Home is not permitted to send a Forwarding type snoop for:

    - Atomic transactions