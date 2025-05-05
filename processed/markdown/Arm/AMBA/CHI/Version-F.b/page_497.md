Table B16.5: Direct\_Cache\_Transfer property options

| Direct\_Cache\_Transfer value | Description                                          |
|-------------------------------|------------------------------------------------------|
| True                          | Direct Cache Transfer transactions are supported     |
| False or Not specified        | Direct Cache Transfer transactions are not supported |

The HN-F is responsible to determine the correct snoop type to use.

### B16.1.6 Data\_Check

A Data\_Check property is used to indicate the DataCheck field is present in the DAT packet.

Table B16.6 shows the Data\_Check property options.

Table B16.6: Data\_Check property options

| Data\_Check value      | Description                                                                                                                                                                                            |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Odd\_Parity            | Data Check is supported and the DataCheck field is present in the DAT packet. </br> If Check\_Type is defined and set to Odd\_Parity\_Byte\_All, the DataCheck field is not present in the DAT packet. |
| False or Not specified | The DataCheck field is not in the DAT packet unless specified by the Check\_Type property                                                                                                              |

### B16.1.7 Check\_Type

A Check\_Type property is used to indicate the protection scheme employed on an interface.

Table B16.7 shows the Check\_Type property options.

Table B16.7: Check\_Type property options

| Check\_Type value       | Description                                                                                                            |
|-------------------------|------------------------------------------------------------------------------------------------------------------------|
| Odd\_Parity\_Byte\_All  | Parity check signals are added to every channel. </br> The signals added are detailed in B9.3 Use of interface parity. |
| Odd\_Parity\_Byte\_Data | The DataCheck field is present in the DAT packet                                                                       |
| False or Not specified  | No checking signals are present on the interface, unless specified by the Data\_Check property                         |