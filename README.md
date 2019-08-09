This repo contains a more universal Micro-Manager arduino firmware for the original Arduino device adapter (NOT Arduino32bitBoards). The firmware is written for some newer arduino boards. It is a work in progress and the firmware isn't thoroughly tested yet. 

There is an other github that has firmware for the newer Arduino32bitBoards device adapter: https://github.com/bonnom/Arduino32BitBoards


# Micro-manager-Arduino
The original micro-manager arduino firmware is specifically written for the Arduino uno and won't work on the newer and faster arduinos. This project aims to rewrite the original firmware to get compatibility with the newer arduino compatible boards. The original firmware and guide can be found on the micro-manager website [link](https://micro-manager.org/wiki/Arduino).

Please keep in mind that many newer Arduino boards gets damaged when 5V is applied on the input pins. 
Voltage level conversion must be needed when using 5V input on not 5V tolerant boards. Also the digital output is 3.3V, most devices that work with 5V input also work fine with 3.3V input but this is not guaranteed.

The Teensy 3.5 is currently the recommended board.

## Advantages of the sketches provided in this repo
* Works on newer and faster boards, pin registers don't have to be used
* Easier to adapt since pin registers aren't used
  * This allows PWM + blanking
  * DAC + blanking
  * Possibility to choose different pins
* No need for external DAC with most boards

## Working Arduino boards:
* ESP32
  - Baudrate: 115200
  - DAC1 on pin 25 and DAC2 on pin 26
  - ADC not implemented
  - Able to set PWM frequency and Resolution
  - Low Price boards available       
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
* ItsyBitsy M4 
  - The ADC does not work at the moment because of DAC implementation
  - Channel 8 has become channel 7
  - KEEP IN MIND: NOT 5V TOLERANT!!
 
### Teensy 3.x Boards
#### All 3.x boards
 - Able to set PWM frequency and Resolution, for more information [link](https://www.pjrc.com/teensy/td_pulse.html)
 - At least one DAC
 - handy: Pinouts page [https://www.pjrc.com/teensy/pinout.html]
 
* Teensy 3.1 & 3.2
  - Seems to work fine, but more testing is needed
  - All currently used pins in the sketch are 5V tolerant
  - Only one DAC on pin A14
  - All other pins are the same as the original UNO firmware

* Teensy 3.5 (Recommended)
  - Not yet tested
  - All currently used pins in the firmware are 5V tolerant
  - DAC1 on pin 21 and DAC2 on pin 22
  - Able to set PWM frequency and Resolution

* Teensy 3.6
  - Uses same sketch as teensy 3.5
  - Faster than teensy 3.5
  - KEEP IN MIND: NOT 5V TOLERANT!!
  
## Not working boards:
  - Esp8266 board
  - Arduino Due
  - Sipeed Maix boards

## To be tested:
 - Teensy LC
 - A SAMD21 board
 - Teensy 3.5 (Very likely Works)
