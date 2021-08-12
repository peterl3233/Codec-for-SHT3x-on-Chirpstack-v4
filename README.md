# Codec-for-SHT3x-on-Chirpstack
Encode and decode codecs for transferring temperature and humidity in 3 bytes 

Here is a short pair of code blocks that can be used on Chirpstack (LoRa) to send temperature and humidity from an SHT3x I2C sensor in 3 bytes.

Encoding (in C) of temperature uses 2 bytes to send temperature as +/- 15 bit + signed number. The humidity is sent a a simple 8 bit signed binary number. Humidity is always positive.  I'm not sure what negative humidity would feel like.

Decoding (in JS) produces an object as required by the Chirpstack Integration Codec.
