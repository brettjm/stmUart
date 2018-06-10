# UART data transfer 
using STM32 and Arduino Uno

## Project details
Arduino listens for UART input data from STM32 in the form of 16 bytes followed by a termination character. When correct input is provided the Arduino will send this data via SPI to Atwinc 1500 to be transferred to remote client via UDP packets.

## Setup
STM32:
```
PC12 --> UART_TX
PD2  --> UART_RX 
```
Arduino:
```
TX1  --> UART_TX
RX0  --> UART_RX
```

## How to use
Load `lc_ap.ino` onto the Arduino Uno.
Connect to `atmelwifi` on client device. Password is set as: `1234567890`
To initiate UDP connection, run the following NetCat command:
```
nc -u 192.168.1.1 80
```
Once connection is established, send the first byte by typing any one character and pressing enter. This initiates the UART data transfer.
Drag `uart_exti/debug/uart_exti.bin` onto the stm32 mounted drive to start transfer.
