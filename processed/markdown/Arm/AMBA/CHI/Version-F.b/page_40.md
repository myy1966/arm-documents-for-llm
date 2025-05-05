**SN**

Subordinate Node. Receives a request from a Home Node, completes the required action, and returns a response. A Subordinate Node is further categorized as:

- **SN-F** Subordinate Node.

    - Used for Normal memory.
    - Can process Non-snoopable Read, Write, and Atomic requests, including exclusive variants of them, and Cache Maintenance Operation (CMO) requests.

- **SN-I** Subordinate Node.

    - Used for peripherals or Normal memory.
    - Can process Non-snoopable Read, Write, and Atomic requests, including exclusive variants of them, and CMO requests.

Figure B1.4 shows various protocol node types connected through an interconnect.

Figure B1.4: Protocol node examples

![Image](page_40/image_000000_9e2acfa8d1cfaa6f28e0937a6ed982ec480b38f4f9f4bc7df28c4f029c287255.png)