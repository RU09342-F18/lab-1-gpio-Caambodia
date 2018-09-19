## Overview:
The main.c files function to blink two LEDs on two separate MSP430 boards with a delay of 30000 clock cycles between blinks for one LED and 50000 clock cycles between blinks for the other.

## Description of Code:
Blinking an LED is a simple task in terms of code. Texas Instruments provides this code in their documentation for the MSP430 boards, and so most of what is used here is their code. Minor adjustments were made to the code to allow for multiple blink of differing frequencies.

The line `P1DIR |= 0x01` sets the pin P1.0 as an output. This is the pin on both boards used where the LED is located, and so we set it as an output so we can control it with the rest of our code. By ORing `P1DIR` with `0x01` or `00000001`, we set the least significant bit in `P1DIR` to 1, which makes it an output. The 0s allow us to avoid disturbing the rest of the bits in `P1DIR`. Another LED was also used on each board, P1.6 on MSP430G2553 and P4.7 on MSP430F5529. The same procedure was used.

The `while` loop here does a few things. The `if` statement checks if integer `i` is not equal to 0, which it should be at the start of the program, in which case it will decrement by 1. When it reaches 0, the program will reset `i` back to 30000 and toggle the LED. The same procedure is used for the other LED, except the delay is different. This loop continues indefinitely.

No input is needed for this code. It will run on its own without any interference. 
