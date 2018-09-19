## Overview:
The main.c files function to blink an LED on two separate MSP430 boards with a delay of 25000 clock cycles between blinks.

## Description of Code:
Blinking an LED is a simple task in terms of code. Texas Instruments provides this code in their documentation for the MSP430 boards, and so most of what is used here is their code.

The line `P1DIR |= 0x01` sets the pin P1.0 as an output. This is the pin on both boards used where the LED is located, and so we set it as an output so we can control it with the rest of our code. By ORing `P1DIR` with `0x01` or `00000001`, we set the least significant bit in `P1DIR` to 1, which makes it an output. The 0s allow us to avoid disturbing the rest of the bits in `P1DIR`.

The `for` loop does two major things: toggle `BIT0`, or `0x01`, of `P1OUT` on or off depending on what its current state is, and count to 25000 based on clock cycles. The loop immediately toggles P1.0, setting it to a 1 to start. This turns the LED on, since we previously set P1.0 to an output. If we had not done this, nothing would happen. Then, integer `i` is set to 25000 and a do-while loop is initialized. The loop decrements `i` by one whenever `i` is not equal to 0. The program effectively waits for 25000 clock cycles, then exits the loop and toggles P1.0 to off. This continues indefinitely.

No input is needed for this code. It will run on its own without any interference.
