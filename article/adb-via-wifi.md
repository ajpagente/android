# Connect to adb via WiFi
The steps in this page is pretty much the same as the one in the reference with a bit of clarification.

## Steps
1) Connect your device to the same WiFi network as the computer you will adb from. Take note of the IP address of your device.
This can be done by checking the WiFi settings or go to Settings > About phone > IP address

2) Connect your device to USB and make sure USB debugging is working. This means enable debugging from your phone, install required drivers on your computer, and authorize debugging from your phone.
The following command should display your device:
```
adb devices
```

3) Run the following command to set the TCP mode port
```
adb tcpip 5555
```

4) Disconnect the device from USB

5) From your computer, connect adb to the device
```
adb connect <device IP address>:5555
```

6) Now you should see your device when running:
```
adb devices
```

# Reference

- [How to Debug Your Android App over WiFi ](https://futurestud.io/tutorials/how-to-debug-your-android-app-over-wifi-without-root)