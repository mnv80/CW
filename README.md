# CW

CW Library for Arduino

This library translates 7-bit ASCII characters into Morse sequences and
sends the result as tones on an output pin.  It also controls a separate 
push-to-talk pin to key up the transmitter.

A PROGMEM translation table represents each ASCII character as a single byte.
The structure of the encoding from MSB to LSB:
 - optional zeros to pad the encoding out to 8 bits
 - mandatory 1-bit to indicate the end of padding
 - Dits and Dahs as binary ones and zeros repectively
i.e. A maps to binary  00000110

Special cases:
 morseError  - send 8 dits
 morseBlank  - send interword gap
 morseIgnore - do nothing - no morse encoding for this character
 
Lower case characters map to uppercase.
Underscores should surround words, but this code doesn't do that.

Use:
1. Instantiate the CW object with parameters:
      pin to use for push-to-talk
      pin to use for sending morse tones
      pin to use for an LED to indicate the transmitter is active
      speed to send the morse, in words per minute
      frequency to use for morse tones, in Hz

2. Call CW.send with parameter the string to be sent.

3. Also available CW.tone to send a specific tone for a specific time.

Dependencies:
   Arduino.h
   Tone.h
