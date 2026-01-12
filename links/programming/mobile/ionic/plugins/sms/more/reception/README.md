
### SMS reception plugin for Phonegap

The Phonegap-SMS-reception-plugin by Pierre-Yves Orban is an Android-specific Cordova/PhoneGap plugin that enables applications to intercept incoming SMS messages.
It provides methods to check if SMS reception is supported (isSupported), start listening for incoming messages (startReception), and stop listening (stopReception).
A notable feature is its ability to abort the broadcast of received messages, preventing them from reaching other applications, including the default SMS app.
This functionality allows developers to handle SMS messages exclusively within their app, which is particularly useful for applications that require private or custom SMS processing.
However, developers should manage this feature carefully to avoid unintended interference with the device's native SMS handling.
The plugin was tested with PhoneGap 2.5 and Android 4.2.2, and it is licensed under the MIT License.

https://github.com/Pyo25/Phonegap-SMS-reception-plugin
