## B5.1 Read transaction flows

This section gives examples of the interconnect protocol flow for Read transactions.

### B5.1.1 Read transactions with DMT and without snoops

For Read transactions without snoops, it is recommended to use DMT.

Figure B5.1 shows an example DMT transaction flow using the ReadShared transaction.

In Figure B5.1, a response from SN-F to HN-F is not required because CompAck from the Requester is used to deallocate the request at Home.

Figure B5.1: DMT Read transaction example without snoops

![Image](page_269/image_000000_a2c0f52a6465f4ad14dcc880f79bef77df6209c318b731cc305dd46ad3977ffd.png)

The steps in the ReadShared transaction flow in Figure B5.1 are:

1. RN-F sends a ReadShared request to HN-F.
2. HN-F sends a ReadNoSnp request to SN-F.
3. SN-F sends a data response directly to RN-F, using CompData\_UC.
4. RN-F sends CompAck to HN-F as the request is ReadShared and requires CompAck to complete the transaction.