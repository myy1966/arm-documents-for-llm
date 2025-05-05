Figure B14.4: Example of a multiple channel unidirectional interface

![Image](page_478/image_000000_b8a2509ce0be2b659a44205c5df72eabc15d9bf4ab6408cc1d22183d0dc1780c.png)

The rules regarding the relationship between the LINKACTIVEREQ and LINKACTIVEACK signals must be applied appropriately across all channels:

- When a state change requires the Transmitter to be able to accept credits, the Transmitter must be able to accept credits on all channels.
- When a state change requires the Receiver to be able to accept flits, the Receiver must be able to accept credits on all channels.
- When the sending of flits must stop before a state change, the sending of flits must stop on all channels.
- When the sending of credits must stop before a state change, the sending of credits must stop on all channels.
- A credit can only be associated with a flit on the same channel.