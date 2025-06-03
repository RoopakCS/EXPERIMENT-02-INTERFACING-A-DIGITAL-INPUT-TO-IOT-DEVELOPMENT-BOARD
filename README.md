# EXPERIMENT-02-INTERFACING-A-DIGITAL-INPUT-OUTPUT-TO-IOT-DEVELOPMENT-BOARD

**DATE: 06/04/2025**

**NAME: Roopak C S**

**ROLL NO: 212223220088**

**DEPARTMENT: B.Tech IT**

## Aim

To Interface a Digital Input (IR pair ) to ARM IOT development board and write a program to obtain the data

## Components required

- STM32 CUBE IDE
- ARM IOT development board
- STM programmer tool

## Theory

The ARM (Advanced RISC Machine) architecture is widely used in microcontrollers and processors due to its efficiency, low power consumption, and high performance. ARM processors follow the Reduced Instruction Set Computing (RISC) design, making them ideal for embedded systems, mobile devices, and IoT applications. Many well-known semiconductor companies, including STMicroelectronics, use ARM-based architectures to develop powerful and energy-efficient microcontrollers.

One such microcontroller is the STM32WLE5JC, which is part of the STM32 family and is based on the ARM Cortex-M4 core. It is specifically designed for LoRaWAN® and other sub-GHz wireless communication applications, making it ideal for IoT and LPWAN (Low Power Wide Area Network) solutions. This microcontroller integrates a LoRa® transceiver, eliminating the need for an external radio module and reducing both cost and power consumption. With a maximum clock speed of 48 MHz, 256 KB of Flash memory, and 64 KB of RAM, it provides enough computing power for real-time data processing and wireless communication.

The STM32WLE5JC is known for its ultra-low power consumption, making it perfect for battery-operated IoT devices such as smart agriculture sensors, environmental monitoring systems, industrial automation, and asset tracking. It supports multiple communication interfaces, including I2C, SPI, and UART, allowing seamless integration with various sensors and peripherals. Additionally, it features built-in security capabilities such as AES 256-bit encryption and a True Random Number Generator (TRNG) for secure data transmission.

With its power-efficient design, built-in LoRaWAN support, and flexible communication options, the STM32WLE5JC is an excellent choice for developers looking to build long-range, low-power IoT applications. It is fully compatible with STM32CubeIDE and LoRaWAN middleware, making development and deployment easier for engineers and students alike.

## Procedure

1. Click on STM 32 CUBE IDE, the following screen will appear
   ![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)

2. Click on FILE, click on new stm 32 project
   ![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)
   ![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)

3. Select the target to be programmed as shown below and click on next
   ![Screenshot 2025-03-11 134231](https://github.com/user-attachments/assets/09e61f3d-224f-4ca8-96d4-7336869df5c7)

4. Select the program name
   ![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)

5. Corresponding ioc file will be generated automatically
   ![Screenshot 2025-03-11 134528](https://github.com/user-attachments/assets/df427edd-e24a-4612-a858-aeae859b379f)

6. Select the appropriate pins as GPIO, in or out, USART or required options and configure
   ![Screenshot 2025-03-11 134617](https://github.com/user-attachments/assets/125ee548-30b1-4c88-932f-adf07984522f)
   ![Screenshot 2025-03-11 134642](https://github.com/user-attachments/assets/0adfbb58-4cad-408a-9300-f4808b53cac4)

7. Click on Ctrl+S, automatically C program will be generated
   ![Screenshot 2025-03-11 134709](https://github.com/user-attachments/assets/70b83b79-1569-4f14-99d5-e2adbb4e692d)

8. Edit the program and as per required

![image](https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png)

9. Use project and build all

![image](https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png)

10. Once the project is bulild

![image](https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png)

11. Open STM32Cube Programmer

![Screenshot 2025-03-11 135208](https://github.com/user-attachments/assets/bb67ab6b-81a5-450c-b170-4276a9b87ef2)

12. Connect the STM board through the COM port, then upload the corresponding project ELF file while ensuring the board is in flash mode, and click on 'Start Program.' After the file download is complete, switch your board to run mode and press the reset button to see the output

## STM 32 CUBE PROGRAM

```c
#include "main.h"
#include "stdbool.h"
bool IRSENSOR;
void IRPAIR();
static void MX_GPIO_Init(void);
int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();
    while (1)
    {
        IRPAIR();
    }
}
void IRPAIR()
{
    IRSENSOR = HAL_GPIO_ReadPin(GPIOB, GPIO_PIN_4);
    if (IRSENSOR == 0)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
        HAL_Delay(1000);
    }
    else
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
        HAL_Delay(1000);
    }
}
```

## OUTPUT

![IMG20250326110915](https://github.com/user-attachments/assets/2704a7cc-1ef4-41c3-b879-b20a0b896934)

![IMG20250326110932](https://github.com/user-attachments/assets/5b98d54d-0d3f-4dc5-b2b0-a2680b2b6d82)

## Result

Interfacing a digital Input (ir pair) with ARM microcontroller based IOT development is executed and the results are verified.
