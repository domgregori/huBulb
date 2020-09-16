# huBulb
Phillips Hue style bulb, 3D printed. ESP8288 with MQTT support.

Started this project because I wanted a Hue type bulb that didn't require a hub or some 3rd party application. I wanted it to integrate with Home Assistant via MQTT and cost less than the Phillips Hue bulbs.

This is a work in progress and uses a modified version of [esp8266-fastled-mqtt by awilhelmer](https://github.com/awilhelmer/esp8266-fastled-mqtt). I'm a novice at C++/Arduino coding so the code can definitely be optimized–apologies for the mess, maybe someone out there would be interesting in contributing to the code? I know there are projects out there that are a complete solution to HA integration such as [McLighting by toblum](https://github.com/toblum/McLighting) but I like better the patterns in this sketch–originally created by [Jason Coon](https://github.com/jasoncoon). It adds some support for HA. But this project will work with any sketch for the ESP8266.


## TODO/Notes
* Optimize code (as in, learn C++)
* Create variables for topics so you don't have to change them manually
* Add color temp support
* Find a cheap higher amp USB power supply that can output at least 3A (LEDs are currently underpowered at full brightness)
* Could use led strip instead to save cost, but the ring LEDs are convenient


## Shopping List
Item | Distributer | Cost | Link
------------ | ------------- | ------------- | -------------
USB Charger | AliExpress | $1.77ea | [Link](https://www.aliexpress.com/item/Dual-USB-Cell-Mobile-Phone-Charger-5V2-1A-1A-EU-US-Plug-Wall-Power-Adapter-for/32807780731.html)
Light Bulb Socket Outlet | Amazon | $5.96 for two | [Link](https://www.amazon.com/gp/product/B002DN6QX2/)
D1 Wemos Mini | AliExpress | $2.73ea | [Link](https://www.aliexpress.com/item/D1-mini-Mini-NodeMcu-4M-bytes-Lua-WIFI-Internet-of-Things-development-board-based-ESP8266-by/32633763949.html)
WS2812 Ring Lights–24,16,8 size | AliExpress | $9.97total | [Link](https://www.aliexpress.com/item/1PCS-Pixel-RGB-LED-Ring-1Bit-8Bit-16Bit-24Bit-35Bit-45Bit-WS2812-5050-RGB-LED-Module/32950477261.html)
2x USB cords | - | - | -
3D Printed Bulb | 3D Printed | - | -

One USB cable powers the D1 Wemos and the 24 bit LED ring, the other powers the other 2 rings.


## To Make
* My STL files are on Thingiverse [here](https://www.thingiverse.com/thing:3635461) to 3D print the bulb. There are 3 pieces: bulb base, LED mount, bulb lid

* Connect D5 on Wemos -> 24bit ring DI. 24bit DO -> 16bit DI. 16bit DO -> 8bit DI.

* Connect 5v and GND from Wemos to 24bit.

* Connect 5v and GND from second USB port to 16bit and 8bit
I connected the ground between 24bit/16bit/8bit but probably does not need that because the USB charger probably shares the ground in the unit.

* Download sketch and change settings in [Settings.h](Settings.h) to match MQTT and your Wifi.

* Without the USB charger plugin, connect and flash the Wemos with my sketch or any other project.

* Push the USB plugs through the bottom of the printed bulb base and and then insert the plugs into the screw outlet. (The fit is meant to be tight so the usb charger doesn't move. I had to take a utility knife to the openings because of my printer.)

* Screw the bulb into an outlet that has power and it should connect if your settings are correct.


## To Use
Use the provided [huBulb.yaml](HA/huBulb.yaml) to integrate into HA

To use via MQTT commands:

Topic | Command | Function
------------ | ------------- | -------------
huBulb/power | on OR off | Turns bulb on or off.
huBulb/brightness | 0-255 | Changes the brightness of bulb.
huBulb/effect | 0-10 | Changes the pattern/effect. 10 is solid color.
huBulb/color | 0-255,0-255,0-255 | Change the color of bulb with r,g,b format. This changes the pattern to 10 as well.


MQTT Status: In JSON format

Topic | Payload
------------ | -------------
huBulb/status | {"status":"online","power":"on","brightness":255,"pattern":0,"color":[159,127,255]}


Object | Value | Comments
------------ | ------------- | -------------
status | online OR offline | Status of connection. If bulb is disconnected, there is a LWT to send offline.
power | on OR off | Bulb is currently on or off.
brightness | 0-255 | Current brightness.
pattern | 0-10 | Current effect.
color | [0-255,0-255,0-255] | An array of the current color set in rgb format.


## Images
![Bulb](/images/IMG_5846.jpg)
![Bulb](/images/IMG_5847.jpg)
![Bulb](/images/IMG_5848.jpg)
![Bulb](/images/IMG_5849.jpg)
![Bulb](/images/IMG_5850.GIF)
