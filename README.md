# Turbine_Tower
This project is to document the hardware & software lighting solution for my friend's vertical wind turbine (WindSpire). 

## Hardware overview
I used [Joel's Antenna2022](https://github.com/jspolsky/Antenna2022) project as a starting point for the hardware. Joel had the idea of transmitting [data and power via Cat6 cable](https://www.blinkylights.blog/2022/05/23/single-cat-6-power-and-data-for-ws2815-led-strips/), utilizing  RS-422 differential signalling for the data lines and use 6 conductors for power, which I thought was a really clean solution. 

### Lighting Controller (cat6 output expander)
For my variant, I wanted to use [PixelBlaze v3](https://shop.electromage.com/products/pixelblaze-v3-standard-wifi-led-controller) as the controller. The PB is responsible for creating the patterns etc and I'm also utilizing one of Ben's output expander boards to get 6 individual lighting channels.

The controller serves three purposes: 
1. Distribute 12V power to the LED strips over Cat6 ethernet cable, 
2. Take the TTL data signal from the PixelBlaze output expander and convert into RS-422 via a MAX485
3. Mount the PB controller and output expander boards directly to my board, which required a 5V linear converter and power bus.

**TODO: Still need to fix the header alignment on the pixelblaze output expander, I just roughed it in for now... SO, dont use it yet.**


Here's the PCB: 
![Output Expander PCB](/main/circuits/PixelBlaze_cat6_expander/PixelBlaze_cat6_expander.png)

Here's the circuit diagram:
![Output Expander PCB](/main/circuits/PixelBlaze_cat6_expander/Schematic_Turbine_LED_Controller.png)

### Receiver boards
These are the same as Joel's implementation, they mount close to each strip.

Input = Cat6 with 12v power and RS422 signal sent from the controller.
Output = 12V power for WS2815 strips and TTL data out

I literally just grabbed Joel's gerbers and ordered a bunch from JLCPCB. Thanks to Joel for making these public and for helping me walk through my first JLCPCB order.
