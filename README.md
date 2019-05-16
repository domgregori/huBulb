# huBulb
Phillips Hue style bulb, 3D printed. ESP8288 with MQTT support.

Started this project because I wanted a Hue type bulb that didn't require a hub or some 3rd party application. I wanted it to integrate with Home Assistant via MQTT and cost less than $15.

This is a work in progress and uses a modified version of [esp8266-fastled-mqtt by awilhelmer](https://github.com/awilhelmer/esp8266-fastled-mqtt). I'm a novice at C++/Arduino coding so the code can definitely be optimized. I know there are projects out there that are a complete solution to HA integration such as [McLighting by toblum](https://github.com/toblum/McLighting) but I like better the patterns in this sketch–originally created by [Jason Coon](https://github.com/jasoncoon). It adds some support for HA.

