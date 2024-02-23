I. CAN Protocol in STM32 (F446RE Nucleo TX and F446RE Nucleo RX)

This tutorial will cover the Basic Can protocol in STM32. Here we will see, how to communicate between two STM32 boards using the CAN protocol. Of course we would need 2 can transceivers (at least) to do that, and that’s why I am using MCP2551 can transceivers.

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/3b9dd4c6-a173-42cd-a1ef-d666f20a37c3)

II. A Little in fo about the CAN Protocol

I am not going to explain every small detail here, instead we will just focus on some important things. For more details about the Protocol, you can google it.

CAN (Controlled Area Network) Protocol is a way of communication between different devices, but under certain rules. These rules must be followed when a message is transmitted over the CAN bus. Here we are going to see these rules.

Shown below is the Standard CAN Frame

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/371fff5d-3493-4314-822f-7e2ddf94cad2)


• Here, Identifier is the ID of the transmitting Device

• RTR (Remote Transmission Request) Specifies if the data is Remote frame or Data frame

• IDE specifies if we are using Standard ID or Extended ID

• r is the Reserved bit

• DLC specifies the data length in Bytes

• Data Field is where we can send the data, which should be upto 8 bytes

• Checksum and DEL are the CRC data and it’s Delimiter

• ACK and DEL is the acknowledgment bit and it’s Delimiter

In this Tutorial, we will see upto the Data Field only. The CRC and ACK will be handled by the HAL Library.


III. Configuration CubeMX Transmitter_Tx (F446RE Nucleo)

    1. Configuration RCC

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/6a520b1f-7045-4a35-b7b1-39e1d76198c5)

    2. Configuration SYS
    
 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/076bdc47-004f-4180-8d4a-fd598bd111ab)

    3. Configuration TIM3 PWM LED

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/676e48f7-78cf-42ca-94d2-7b0e6a2f5945)

    4. Configuration TIM4 (Time Base)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/fa3407e1-d51e-4626-8cd3-b102ce4451e1)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/2b74a43d-9f7a-4c65-9dcf-fb6a86b0721d)

    5. Configuration NVIC

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/c8f9059f-eadf-4598-9e01-0e1b2df2fdf3)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/51540032-c82f-43c0-962d-bc82285122f3)

    6. Configuration GPIO

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/2afd1d88-c478-4b77-8c5f-be28cfa6465a)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/8c0e5364-946b-4f13-a1ff-f2c184a40c53)

    7. Configuration CAN

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/807fabb7-c083-494f-9200-9a9bc234772d)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/69de2041-e97f-45b3-90a6-4a03c3507d76)

    8. Configuration CLOCK

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/3374fd8d-24e9-47ca-a9d2-84af0e1b861c)

    9. Code in main.c (Tx)

 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/c4a22115-3d20-4701-9beb-2bb76f8e158c)

 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/0de0d775-885c-421b-8e96-e8ce8538475e)

 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/569f00d3-8535-4696-820b-b1e7abeaefdb)

 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/6f31ddc5-68b5-4d7b-b146-ed4ce46c79fa)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/4c02b5a4-d451-40c0-8e48-16f2b933a48b)

    10. Code can.c in (Tx)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/d99d4f8e-dd96-4263-85d4-bde5132f82fa)


IV. Configuration CubeMX Receiver_Rx (F446RE Nucleo)

    1. Configuration RCC

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/b8433c8c-5ca9-4721-9c39-957d744d3a5c)

    2. Configuration SYS

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/0b5cf2fd-7104-4125-aac4-904d14a21ac7)

    3. Configuration NVIC

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/4bf3f19b-5a14-41ae-82e7-13701e9b3e1e)
    
    4. Configuration GPIO

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/2bb062b5-1bf5-4cea-a206-79f65b2b815e)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/71c4013b-b1ad-403e-826c-e37ad56c062d)

    5. Configuration TIM3 PWM LED

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/17683e51-2d86-4b02-8453-650925c942c1)

    6. Configuration TIM4 (Time base)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/6977840e-d98d-4d70-9c65-628264d409c1)

    7. Configuration CAN

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/4b7607be-25de-4643-9d13-4ab32a894d80)

    8. Configuration CLOCK

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/fff4f239-1e50-46ab-a50f-848a9441da71)

    9. Configuration CAN

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/d28813e1-41f4-4f85-9524-71c07f643f79)

    10. Code Rx main.c

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/fdf6c9a6-4693-4d47-a695-41a4cc039cdc)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/2f4e4f1e-b62a-465a-b1bc-e82e2ecdbf90)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/573f4003-9524-4bdb-85e6-07f41660fa08)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/034f377d-1512-4bc3-a373-edb3ca4600b9)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/597c5482-097d-45c2-ba86-376f19a9ddc4)

    11. Code can.c in (Rx)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/b41cafc1-820f-4320-957b-ac6aa3f7a136)


VI. Filtter Configuration 

In order to reduce CPU Load to filter out messages, the STM32 have the Filters built inside the CAN peripheral. Let’s Check them out

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/8d630815-0b91-459b-a817-fa3ba6e6240c)

1. FilterActivation specifies if we want to enable Filters or not. Obviously we have to enable them

2. SlaveStartFilterBank specifies How many Filter Banks do we want to assign to CAN1. Basically the controllers with dual CAN peripheral have 28 Filter Banks, which can be distributed between these 2 CAN. Here I am assigning 20 Filter Banks to the CAN1, and Rest to the CAN 2.

       •  This parameter is useless for the controllers with single CAN peripheral. And these Controllers have 14 Filter Banks ( 0 to 13)

3. FilterBank specifies which Filter Bank do we want to use for the filter Process. Here I have assigned 20 Banks for CAN 1, and I can only choose Out of these 20 Banks. So I am choosing Bank number 18.

       • In case of Single CAN Peripheral, you can choose any value between 0 to 13

4. FilterFIFOAssignment specifies which FIFO are we going to use for the Receive message. Generally we have 2 FIFOs ( FIFO 0, and FIFO 1). I am choosing FIFO 0

5. FilterMode specifies which type of Filter do we want to use. We have 2 types of filters in STM32. MASK MODE, where the Mask register will be used to compare some particular bits in the ID register to the incoming ID. And the LIST MODE, where the incoming ID is directly compared with the ID set in the ID Register.

        • I am using MASK Mode here, as It seems to be more useful

6. FilterScale specifies If we want to use one 32 bit Filter Register, or 2 16 bit Filter Registers.

        • I am using one 32 Bit Register here.

7. FilterIdHigh is the Higher 16 Bits of the ID register. The value set in this register will be compared to the incoming Identifier.

       • Here I have decided to only compare the STD ID of the incoming message, and that’s why I am shifting the value by 5. The STD ID starts from 5th bit in the ID HIGH Register

8. FilterMaskIdHigh is the Higher 16 Bits of the MASK register. The value set in this register will enable the comparison of that particular bit in the ID register to that of the incoming ID.


VII. Connection and Diagram

The connection between F446 Nucleo TX and F446 Nucleo RX is shown below.

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/c98fb349-2686-4ecf-8a43-cceade41459e)

• Here the Tx and Rx from the Transceivers are connected to PA12 and PA11 of the Respective controllers

• CANH and CANL are connected to each other

• Also, there is 120 ohms Resistance at each node. This is very important, or else you will not get the data.

VIII. Real Connection and Diagram

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/99c7fbf8-b6e7-4e48-bab9-26bcbd2aff5a)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/7cb6e4e2-26b7-4bed-9306-8635c3245925)


 IX. VDO Testing 

        • VDO TESTING 1

 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/16ac4410-46ab-46ad-8bf7-a329a75efb6b)

         • VDO TESTING 2
         
 ![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/0bd4142a-df47-45a8-ba8e-4805c2ac85d0)

![image](https://github.com/TepmarotdanielZ/CAN-BUS/assets/139426571/f1619105-6207-4020-9841-e1685f4ce9cb)





