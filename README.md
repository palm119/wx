# xESP12F

Extension for ESP8266-12F Wifi module.

Update:
0.0.1：
初始化版本.

## Feature

- Control wifi access from microbit
- MQTT control, subscribe publish from microbit
- RESTFul PUT/GET request to online services, like IFTTT, thingspeak and so on

## Test Code
```
xESP12F.on_wifi_connected(function () {
    xESP12F.mqtt_connect("iot.kittenbot.cn", "microbit")
})
xESP12F.on_mqtt_connected(function () {
    xESP12F.mqtt_subscribe("/test/hello")
})
xESP12F.on_mqtt_topic_data(function (topic, data) {
    if (topic == "/test/hello") {
        if (data == "1") {
            basic.showIcon(IconNames.Heart)
        } else {
            basic.showIcon(IconNames.SmallHeart)
        }
    }
})
input.onButtonPressed(Button.A, function () {
    xESP12F.mqtt_publish("/test/wendu", "22")
})
xESP12F.wifi_init(SerialPin.P1, SerialPin.P2)
xESP12F.wifi_join("tets", "123456")
```

----------

## License

MIT

## Supported targets

* for PXT/microbit
(The metadata above is needed for package search.)
