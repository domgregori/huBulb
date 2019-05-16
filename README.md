# huBulb
Phillips Hue style bulb, 3D printed. ESP8288 with MQTT support.

Started this project because I wanted a Hue type bulb that didn't require a hub or some 3rd party application. I wanted it to integrate with Home Assistant via MQTT and cost less than $15.

This is a work in progress and uses a modified version of [esp8266-fastled-mqtt by awilhelmer](https://github.com/awilhelmer/esp8266-fastled-mqtt). I'm a novice at C++/Arduino coding so the code can definitely be optimized–apologies for the mess, maybe someone out there would be interesting in contributing to the code? I know there are projects out there that are a complete solution to HA integration such as [McLighting by toblum](https://github.com/toblum/McLighting) but I like better the patterns in this sketch–originally created by [Jason Coon](https://github.com/jasoncoon). It adds some support for HA. But this project will work with any sketch for the ESP8266.

## TODO/Notes
* Optimize code
* Create variables for topics so you don't have to change them manually
* Add color temp support
* Find a cheap higher amp USB power supply that can output at least 3A (LEDs are currently underpowered at full brightness)
* Could use led strip instead to save cost, but the ring LEDs are convenient


## Shopping List
Item | Distributer | Cost | Link
------------ | ------------- | ------------- | -------------
USB Charger | AliExpress | $1.77ea | [Link](https://www.aliexpress.com/item/Dual-USB-Cell-Mobile-Phone-Charger-5V2-1A-1A-EU-US-Plug-Wall-Power-Adapter-for/32807780731.html)
Light Bulb Socket Outlet | Amazon | $2.75ea | [Link](https://www.amazon.com/gp/product/B01NCVQBB9)
D1 Wemos Mini | AliExpress | $2.73ea | [Link](https://www.aliexpress.com/item/D1-mini-Mini-NodeMcu-4M-bytes-Lua-WIFI-Internet-of-Things-development-board-based-ESP8266-by/32633763949.html)
WS2812 Ring Lights–24,16,8 size | AliExpress | $9.97total | [Link](https://www.aliexpress.com/item/1PCS-Pixel-RGB-LED-Ring-1Bit-8Bit-16Bit-24Bit-35Bit-45Bit-WS2812-5050-RGB-LED-Module/32950477261.html)
2x USB cords | - | - | -
3D Printed Bulb | 3D Printed | - | -

One USB cable powers the D1 Wemos and the 24 bit LED ring, the other powers the other 2 rings.

## To Make
