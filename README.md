# Codec-for-SHT3x-on-Chirpstack V4
Encode and decode codecs for transferring temperature and humidity in 3 bytes.  Usually developers send 2, 16 bit binary numbers to handle temperature and humidity.  This routine sends just 3 bytes because humidity ( at least in my case) is good enough between 0 and 100 percent as a simple integer. This is used with the SHT3x sensor and the sensirion/arduino-sht @ ^1.2.0 Library.

Here is a short pair of code blocks that can be used on Chirpstack (LoRa) to send temperature and humidity from an SHT3x I2C sensor in 3 bytes.  They probably work on TTN but I have not tested or tried it. TTN's syntax is slightly different.

Encoding (in C) of temperature uses 2 bytes to send: 
Temperature (+100) x 100) as a 16 bit unsigned signed number. The humidity is sent a a simple 8 bit signed binary number. Humidity is always positive.  I'm not sure what negative humidity would feel like.

Decoding (in JS) produces an object as required by the Chirpstack Integration Codec. The temperature value is scaled (back) by 100 and then reduced by 100 to match the encoding method.
