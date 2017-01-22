This arduino sketch will simulate a VGA monitor by sending a 128 byte
byte-array containing EDID info when requested by the operating system. 


In order for this program to work, the i2c transmit buffer length constants must be changed in
two files. The Wire library has two buffers it uses for i2c transmissions

"BUFFER_LENGTH" in
"arduino_install_folder/hardware/arduino/avr/libraries/Wire/src/Wire.h" and

"TWI_BUFFER_LENGTH" in
"arduino_install_folder/hardware/arduino/avr/libraries/Wire/src/utility/twi.h"

Both of these must be changed from 32 to 128 to be able to transmit the edid byte array in
one shot.
   
To test this program, you can directly wire SDA(pin 12),SCL(pin 15) and GND(pin 6) pins from your computers VGA port
directly into the corresponding pins on the arduino.

The EDID in this sketch is for an eMac CRT but can theoretically be replaced 
by any valid 128 byte EDID.
