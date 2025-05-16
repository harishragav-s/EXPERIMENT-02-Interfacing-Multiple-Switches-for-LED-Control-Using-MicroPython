# EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython


 
## NAME:HARISH RAGAV S

## DEPARTMENT: CSE(IOT)

## ROLL NO:212222110013

## AIM

To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED

Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

## THEORY



FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

WORKING PRINCIPLE

The switches are connected as inputs to GPIO pins of the Pico.

The LEDs are connected as outputs.

A MicroPython script reads the switch states and controls the LEDs accordingly.

### CIRCUIT DIAGRAM
 ![image](https://github.com/user-attachments/assets/1c7234b9-5041-4156-94b8-0b846adb6b8e)
    Figure-01 circuit diagram of digital input interface 


Connect switch 1 to GP2 and switch 2 to GP3.

Connect LED 1 to GP14 via a 330Ω resistor.

Connect LED 2 to GP17 via a 330Ω resistor.

Connect the other terminals of the switches to GND.

## PROGRAM (MicroPython)
````
import machine import Pin
from time import sleep
switch1=Pin(2, Pin.IN)
switch2=Pin(3, Pin.IN)
led = Pin(15,Pin.OUT)
led2 = Pin(16, Pin.OUT)
   
while True:
    sw1_state= switch1.value()
    sw2_state= switch2.value()
    print("Switch 1 state:",sw1_state)
    print("Switch 2 state:",sw2_state)
    led.value(0)
    if sw1_state==1 and sw2_state==1:
        led.value(0)
        led2.value(0)
    elif sw1_state==1:
            led.value(1)
            sleep(0.5)
            led.value(0)
            led2.value(0)
    elif sw2_state==1:
            led.value(0)
            led2.value(1)
            sleep(0.5)
            led2.value(0)
    sleep(0.5)

````

## OUTPUT
![419930930-24e9b62f-3bf0-475a-b173-163452365d28](https://github.com/user-attachments/assets/d61af4fc-5d58-4d0c-a646-657f632fb403)



FIGURE-02: CIRCUIT CONNECTION
![419931543-0989bd52-6a04-49a3-af67-17481da90e1a](https://github.com/user-attachments/assets/51f3c011-392b-497b-8480-55270f0632cc)

FIGURE-03: CODE EXECUTION OUTPUT
![419932435-d5082da3-282e-4b9b-98a9-c167b45fe5a4](https://github.com/user-attachments/assets/09a6c2e8-7f1c-48c3-ae11-1145637f1fcf)

FIGURE-04: LED STATUS BASED ON SWITCH INPUTS
![419932787-e21978a4-aad4-442b-b44c-226b57cb8693](https://github.com/user-attachments/assets/cc55181d-df24-4e44-939e-d341383fb91d)

## TIMING DIGAGRAM 

![419935571-8922f88b-a39d-494f-a4c7-26d2017b7c21](https://github.com/user-attachments/assets/893420e9-dda6-447a-b921-db8aff584e9c)

## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

