# EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython


 
## NAME: ARJUN K

## DEPARTMENT:CSE

## ROLL NO:212224040028

## DATE OF EXPERIMENT:03-03-2025

## AIM:

To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED:

Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

## THEORY:



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

## PROGRAM (MicroPython):
```
from machine import Pin
from time import sleep
switch1=Pin(2,Pin.IN)
switch2=Pin(3,Pin.IN)
led1 = Pin(15,Pin.OUT)
led2 = Pin(16,Pin.OUT)
while True:
    sw1_state = switch1.value()
    sw2_state = switch2.value()
    print("switch 1 state:",sw1_state)
    print("switch 2 state:",sw2_state)
    led1.value(0)

    if sw1_state== 1 and sw2_state== 1:
        led1.value(0)
        led2.value(0)

    elif sw1_state== 1:
        led1.value(1)
        sleep(0.5)
        led1.value(0)
        led2.value(0)

    elif sw2_state== 1:
        led1.value(0)
        led2.value(1)
        sleep(0.5)
        led2.value(0)

    sleep(0.5)

```
## OUTPUT:
Output 1(0-0):
![Screenshot 2025-03-03 105439](https://github.com/user-attachments/assets/140b7896-2fd9-449a-ae31-42f2d8fd2811)
Output 2(1-0):
![Screenshot 2025-03-03 105510](https://github.com/user-attachments/assets/328fb852-a3b4-4fea-ad8d-fa441e77e7dd)
Output 3(0-1):
![Screenshot 2025-03-03 105527](https://github.com/user-attachments/assets/06140e87-4f20-4b2b-b2de-180527348f5b)
Output 4(1-1):
![Screenshot 2025-03-03 105642](https://github.com/user-attachments/assets/f5e45f77-14bc-465f-8dc8-12cb550d652d)
## TIMING DIGAGRAM :
![edge exp2](https://github.com/user-attachments/assets/8f50470e-7004-417b-a47a-696512b3435e)
## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

