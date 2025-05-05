## B3.1 System Address Map, SAM

Requesters must have a System Address Map (SAM) to determine the TgtID of a request. Requesters could be Request Nodes or Home Nodes. The scope of the SAM could be as simple as providing a fixed node ID value to all the outgoing requests.

The exact format and structure of the SAM is IMPLEMENTATION DEFINED and is outside the scope of this specification.

The SAM must provide a complete decode of the entire address space. It is recommended that any address that does not correspond to a physical component is sent to an agent that can provide an appropriate error response.