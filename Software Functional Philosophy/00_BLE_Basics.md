The BLE communication is programmed to perform with the acknowledge (ACK) function, meaning when the sender sends the data, upon successful reception from the receiver, the receiver sends ACK to the sender. These states of communication are reported by CPU2 and can be used to evaluate the status of communication and take necessary action. Also, the communication is encrypted for safety against snooping. The program uses a default key and initialization vector for encryption.

The table below shows all the different states that are reported by CPU2:
| State	| Description |
| --- | --- |
| TX_OK_BUSY	| Transmission succeeded, Radio Busy |
| TX_OK_READY	| Transmission succeeded, Radio Ready |
| TX_FAIL_BUSY	| Transmission failed, Radio Busy |
| TX_FAIL_READY	| Transmission failed, Radio Ready |
| RX_OK_BUSY	| Reception succeeded, Radio Busy |
| RX_OK_READY	| Reception succeeded, Radio Ready |
| RX_FAIL_BUSY	| Reception failed, Radio Busy |
| RX_FAIL_READY	| Reception failed, Radio Ready |
| RX_TIMEOUT_BUSY	| Reception timed out, Radio Busy |
| RX_TIMEOUT_READY	| Reception timed out, Radio Ready |
| RX_CRC_KO_READY	| Reception failed CRC*, Radio Busy |
| RX_CRC_KO_BUSY	| Reception failed CRC, Radio Ready |

*CRC stands for Cyclic Redundancy Check

For successful transmission, the sender MCU CPU2 goes through the following states:

i.	TX_OK_BUSY: CPU2 is sending data, therefore it is busy.

ii.	RX_OK_READY: CPU2 has received data from the receiver, the CPU1 checks if the data received is in fact ACK; if it is ACK, the communication is evaluated as successful.

If CPU2 returns any other state listed in table after TX_OK_BUSY, or if the data received is not ACK, the communication is evaluated as failed.

For successful reception, the receiver MCU CPU2 goes through the following states:

i.	RX_OK_BUSY: CPU2 has received data, CPU2 is sending ACK and it therefore busy

ii.	TX_OK_READY: CPU2 has sent ACK to the sender.

If CPU2 returns any other state listed in table after RX_OK_BUSY, the communication is evaluated as failed.
