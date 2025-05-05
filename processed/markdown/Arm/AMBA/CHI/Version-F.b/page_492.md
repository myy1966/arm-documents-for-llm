    - All data packets are sent for snoops and Forwarding snoops.

- Keep servicing Snoop requests until **SYSCOACK** is sampled LOW at T4.

**SACTIVE** must be asserted during coherency state transition periods to guarantee the **SYSCOACK** transition occurs. See B14.7 Protocol layer activity indication.

### B15.2.2 Interconnect rules

Referring to Figure B15.2:

The interconnect must do the following when **SYSCOREQ** is sampled HIGH:

- Set **SYSCOACK** HIGH without waiting for responses to any previous Snoop requests after **SYSCOREQ** goes HIGH.
- Be able to service coherent data accesses from the interface when **SYSCOACK** is HIGH at T2.

The interconnect must do the following when **SYSCOREQ** is sampled LOW:

- Stop issuing new Snoop requests in a timely manner.
- Complete all snoop accesses to the interface before it sets *SYSCOACK* LOW at T4.

### B15.2.3 Protocol states

Table B15.1 shows the interface states and the rules that the Requester must follow in relation to the interface state.

Table B15.1: System coherency interface states

| State name         | SYSCOREQ | SYSCOACK | Request Node                                                                                                                                                                                                               | Interconnect                 |
|--------------------|----------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------|
| Coherency Disabled | 0        | 0        | Caches must not contain coherent data. </br> Must not issue transactions that permit the Request Node to cache a coherent location. </br> Must not send DVM transactions. </br> Not required to respond to Snoop requests. | Must not send Snoop requests |
| Coherency Connect  | 1        | 0        | Caches must not contain coherent data. </br> Must not issue transactions that permit the Request Node to cache a coherent location. </br> Must not send DVM transactions. </br> Must respond to Snoop requests.            | Can send Snoop requests      |

Continued on next page