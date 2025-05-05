- Protocol credits are for the combined TXREQ channel.
- There is no support for powering down a subchannel individually.
- The two parts of a DVM snoop can come on either subchannel. Each part can be on a different subchannels.
- The number of subchannels on two connected interfaces must match.
- There must be only one set of SACTIVE LINKACTIVE, and SYSCOREQ/SYSCOACK signals, and optional broadcast control pins.
- Interface property CCF\_Wrap\_Order is not permitted to be set to True when the interface includes replicated DAT channels.

> **_NOTE:_** When a channel has been replicated on an interface, it is IMPLEMENTATION DEFINED which of the subchannels is used for a transfer.