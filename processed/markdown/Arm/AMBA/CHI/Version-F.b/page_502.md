Table B16.17 Continued from previous page

| PBHA\_Support value    | Description                                                                        |
|------------------------|------------------------------------------------------------------------------------|
| False or Not specified | PBHA feature is not supported. </br >No PBHA signals are present on the interface. |

### B16.1.19 DVM\_Support

A DVM\_Support property is used to indicate Arm ARM specification supported by a given component.

Table B16.18 shows the DVM\_Support property options.

Table B16.18: DVM\_Support property options

| DVM\_Support value     | Description                                                         |
|------------------------|---------------------------------------------------------------------|
| DVM\_v8                | The component supports DVM transactions required to support Armv8   |
| DVM\_v8.1              | The component supports DVM transactions required to support Armv8.1 |
| DVM\_v8.4              | The component supports DVM transactions required to support Armv8.4 |
| DVM\_v9.2              | The component supports DVM transactions required to support Armv9.2 |
| False or Not specified | The component does not support DVM transactions                     |

In a system with heterogeneous components, the system configuration is responsible to determine the lowest common DVM specification supported in the system. The interconnect must have the knowledge of this lowest common denominator value by means of configuration, straps, parameterization, or some other IMPLEMENTATION DEFINED method.

To avoid deadlocks and denial of service, the interconnect must detect unsupported DVM operations. The interconnect must suppress unsupported DVM operation propagation and respond in a protocol-compliant manner. Error indication in such a response is optional.

For further information, see Chapter B8 DVM Operations.