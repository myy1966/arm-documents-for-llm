## B9.4 Hardware and software error categories

This specification defines two error categories:

- Software-based
- Hardware-based

### B9.4.1 Software-based error

A software-based error occurs when multiple accesses to the same location are made with incorrect or mismatched Snoopable or Memory attributes. See B2.7.7 Mismatched Memory attributes.

A software-based error can cause a loss of coherency and the corruption of data values. It is required that the system does not deadlock for a software-based error, and that transactions always progress through a system in a timely manner.

A software-based error, for an access within one 4KB memory region, must not cause data corruption within a different 4KB memory region.

For locations held in Normal memory, the use of appropriate stores and software cache maintenance can be used to return memory locations to a defined state.

When accessing a peripheral device the correct operation of the peripheral cannot be guaranteed. The only requirement is that the peripheral continues to respond to transactions in a protocol-compliant manner. The sequence of events that could be required to return a peripheral device that has been accessed incorrectly to a known working state is IMPLEMENTATION DEFINED.

### B9.4.2 Hardware-based error

A hardware-based error is defined as any protocol error that is not a software-based error.

> **_Caution:_** If a hardware-based error occurs, recovery from the error is not guaranteed. The system could crash, lock-up, or suffer some other non-recoverable failure.