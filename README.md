# etbl-assignment-02-solved
**TO GET THIS SOLUTION VISIT:** [ETBL Assignment 02 Solved](https://www.ankitcodinghub.com/product/etbl-electronic-technologies-and-biosensors-laboratory-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;127137&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;ETBL Assignment 02 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
&nbsp;

Objective

In this assignment you are required to create a project using PSoC Creator, the CY8CKIT-059 KIT, a RGB LED and three 330 Ohm resistors.

Context

The LTEBS srl asks you to design a system able to control the color of the RGB LED through a serial port. The first time the system is powered after programming, the RGB LED should be on with a “black” color (RGB: 0,0,0). Then, with the protocol described here below, the color emitted with the RGB LED could be changed by sending commands through the serial port. The RGB LED has a common anode configuration, and must be connected as follows:

The pins 2.5, 2.6, and 2.7 are the pins on the CY8CKIT-059 KIT that you must use to control the channels of the RGB LED.

Connections

The RED channel of the RGB Led must be connected to pin 2.7. The GREEN channel of the RGB Led must be connected to pin 2.6. The BLUE channel of the RGB Led must be connected to pin 2.5. The UART must use the pins 12.6 and 12.7 in order to communicate through the KitProg.

Serial Port Communication

1. RGB Color Packet

The commands to be sent through the serial port must be structured as follows: Byte (HEX) | Description | :———–:|————-| 0xA0 |

Packet header (decimal value: 160) R | Red light (0x00-0xFF in Hex, 0-255 in decimal) G | Green light (0x00-0xFF in Hex, 0-255 in decimal) B | Blue light (0x00-0xFF in Hex, 0-255 in decimal) 0xC0 | Packet tail (decimal value: 192)

The UART peripheral must be configured so as to trigger an interrupt when receiving a single byte (you can configure this kind of behaviour in the Advanced Tab of the UART component in PSoC Creator). A simple state machine will then allow you to perform a parsing of the received data packet:

Depending on the received bytes, it is necessary to control the duty cycle of the PWM components that are connected to the RGB LED channels. Here are some working examples: Received Packet | Color | :————–:|——-| [0xA0, 0xFF, 0x00, 0x00, 0xC0] | RED [0xA0, 0x00, 0xFF, 0x00, 0xC0] | GREEN [0xA0, 0x7F, 0x00, 0x7F, 0xC0] | PURPLE

If the system finds itself in one of the intermediate states of the state machine (i.e., exlcuding the IDLE and TAIL states), a 5 seconds timeout must be started in order to allow the system to go back to the idle state if no command is received in 5 seconds.

2. Timeout Configuration

Byte (HEX) | Description | :———–:|————-| 0xA1 | Packet header (decimal value: 161) T | Number of seconds for timeout (1-20) 0xC0 | Packet tail (decimal value: 192)

3. Connection Command

Upon receiving the character v, the system must send this string on the serial port:

RGB LED Program $$$

This is required for the subsequent testing of the program through a simple GUI.

Test

You can test your program using a GUI designed in Kivy that we provide to you. You are required to download the zip file of the GUI, named RGB_Led_Control.zip from the course webpage. Unzip the file, and inside the folder rgbledcontrol, double click on rgbcontrol.exe. The GUI will automatically scan all the available serial ports, connect to the right one and will allow you to send a new color with the described packet structure.

The GUI only work on Windows. For those of you who are using VirtualBox, please configure the display settings as follows:

When using the GUI, please make sure to close all the active serial connections with the CY8CKIT-059 (e.g., CoolTerm, Bridge Control Panel,

…)

Setup and Assignment Delivery

One student from the team forks this repository

Each team member clones the forked repository by entering the following command in the terminal:

git clone https://github.com/[your_username]/AY2021_II_HW_02.git – Open up the workspace in PSoC Creator –

Evaluation

Additional Resources:

PSoC PWM Component Datasheet

PSoC 5LP Interrupts

PSoC 101 Video Tutorial
