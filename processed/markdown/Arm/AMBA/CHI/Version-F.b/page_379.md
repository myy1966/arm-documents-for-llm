## B11.1 Quality of Service (QoS) mechanism

### B11.1.1 Overview

A system could utilize a QoS scheme to achieve:

- A guaranteed maximum latency for transactions in a particular stream.
- Minimum bandwidth guarantees for a stream of requests.
- Best effort value of bandwidth and latency provided to requests of a particular stream.

The low latency, or guaranteed throughput requirements, required to meet system QoS demands are primarily the responsibility of the transaction end points with support from the intermediate interconnect. The protocol supports this by defining a QoS priority value for packets and controlling request flow using a defined credit mechanism.

### B11.1.2 QoS priority value

A 4-bit value is used to prioritize the processing of the packets at protocol nodes and within the interconnect. The QoS Priority Value (PV) for packets is assigned by the source of the transaction. In typical usage models, this value depends on the source type and the class of traffic, with ascending values of QoS indicating a higher priority level. The source could also dynamically vary this value, depending on some accumulated latency and required throughput metric.

### B11.1.3 Repeating a transaction with a higher QoS value

When a transaction has been sent with a particular QoS value, the same transaction can be sent again with a different QoS value, typically higher. The Completer is required to handle this situation as multiple different requests.

In this instance, if one of the transactions receives a RetryAck response, the transaction can be canceled and the credit returned. See B2.9.1 Credit Return.