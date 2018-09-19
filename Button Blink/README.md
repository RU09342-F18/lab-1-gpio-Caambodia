## Overview:
The main.c files function to turn an LED on when a button is pressed and turn it off when that button is released. Effectively, this code is just a momentary switch.

## Description of Code:
Blinking an LED is a simple task in terms of code. Texas Instruments provides this code in their documentation for the MSP430 boards, and so most of what is used here is their code. Minor adjustments were made to the code to allow for button blink.

The line `P1DIR |= 0x01` sets the pin P1.0 as an output. This is the pin on both boards used where the LED is located, and so we set it as an output so we can control it with the rest of our code. By ORing `P1DIR` with `0x01` or `00000001`, we set the least significant bit in `P1DIR` to 1, which makes it an output. The 0s allow us to avoid disturbing the rest of the bits in `P1DIR`. In order to set the button on P1.3 as an input, we must AND `P1DIR` with `~BIT3` or `11110111`, setting the bit to 0. On the MSP430F5529, the button is found on P4.7.

In order to use a button, we also have to enable a pull-down/pull-up resistor. On the MSP430G2553, we run the line `P1REN |= BIT3`, which enables the pull-down resistor. Since the resistor is set as a pull-down resistor by running `P1OUT &= ~BIT3`, the bit is 0 by default and this line is not neccesary. However, on the MSP430F5529, a pull-up resistor is required on P4.7. In this case, we must run `P1OUT |= BIT7` to set the resistor as a pull-up.

The `for` loop simply set j as the `P1IN & BIT3`, which means that we should only ever see `j` as a 0 or 8. Therefore, we can watch for when this switches and toggle the LED when the button is pressed. This code makes the button a momentary switch, which means that it will only activate the LED while the button is being pressed down. `P1IN & BIT1` is used instead on MSP430F5529.

No input is needed for this code. It will run on its own without any interference. 
