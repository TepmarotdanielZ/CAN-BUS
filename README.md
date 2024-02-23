I. CAN Protocol in STM32 (F446 Nucleo TX and F446 Nucleo RX)

This tutorial will cover the Basic Can protocol in STM32. Here we will see, how to communicate between two STM32 boards using the CAN protocol. Of course we would need 2 can transceivers (at least) to do that, and that’s why I am using MCP2551 can transceivers.

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/3b9dd4c6-a173-42cd-a1ef-d666f20a37c3)

II. A Little in fo about the CAN Protocol

I am not going to explain every small detail here, instead we will just focus on some important things. For more details about the Protocol, you can google it.

CAN (Controlled Area Network) Protocol is a way of communication between different devices, but under certain rules. These rules must be followed when a message is transmitted over the CAN bus. Here we are going to see these rules.

Shown below is the Standard CAN Frame

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/18f4638d-603d-4ef2-8932-787a9434f02d)


• Here, Identifier is the ID of the transmitting Device
• RTR (Remote Transmission Request) Specifies if the data is Remote frame or Data frame
• IDE specifies if we are using Standard ID or Extended ID
• r is the Reserved bit
• DLC specifies the data length in Bytes
• Data Field is where we can send the data, which should be upto 8 bytes
• Checksum and DEL are the CRC data and it’s Delimiter
• ACK and DEL is the acknowledgment bit and it’s Delimiter

In this Tutorial, we will see upto the Data Field only. The CRC and ACK will be handled by the HAL Library.

III. Connection and Diagram

The connection between F446 Nucleo TX and F446 Nucleo RX is shown below.

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/c98fb349-2686-4ecf-8a43-cceade41459e)

• Here the Tx and Rx from the Transceivers are connected to PA12 and PA11 of the Respective controllers

• CANH and CANL are connected to each other

• Also, there is 120 ohms Resistance at each node. This is very important, or else you will not get the data.
