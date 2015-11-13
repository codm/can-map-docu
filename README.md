# can-map-docu

## Base
The CAN-MAP Protocol is based on ISO-TP (https://en.wikipedia.org/wiki/ISO_15765-2). The Problem we had with using ISO-TP is that there is no possibility to directly adress a specific device with multiple messages in a way that this device is able to internally sort the messages by the sender.

Since we had the idea to use ISO-TP for our project and had a nearly complete implementation, we based our own Protocol on ISO-TP.

## Changes
There is nearly nothing we changed, but a **VERY** important byte:

ISO-TP Frames are structured like this:

`[CAN_ID]       | [EXTENDED_ID] [TYPE | LEN] [LENGTH] [DATA PAYLOAD]`

We removed the EXTENDED CAN ID and replaced it with our SENDER_ID

`[RECEIVER_ID]  | [SENDER_ID]   [TYPE | LEN] [LENGTH] [DATA PAYLOAD]`

We also changed the semantic of the CAN_ID to a RECEIVER_ID. The effect is that you can sort every message you get by the sender ID it comes from and you still got the possibility to keep 250 devices on the bus.

The Flow Control Frame is working the same way.

## ISO-TP

If you want to have further information on how ISO-TP is working you can consider following links:
* [Wikipedia](https://en.wikipedia.org/wiki/ISO_15765-2)
* [Emotive](https://www.emotive.de/doc/car-diagnostic-systems/protocols/tp/isotp)
* [Google Books (GERMAN)](https://books.google.de/books?id=L0v7AwAAQBAJ&lpg=PA153&ots=V1lUHsefky&dq=ISO-TP&hl=de&pg=PA155#v=onepage&q=ISO-TP&f=false)

## CAN-MAP
* https://github.com/codm/canmap-avr
* https://github.com/codm/canmapd
