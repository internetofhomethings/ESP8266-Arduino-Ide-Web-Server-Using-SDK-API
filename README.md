<h2><strong>ESP8266 Web Server Using SDK API</strong></h2>

This project provides a Web Server Framework using either the Arduino Wifi Library or the EspressIf SDK API.

Setup:

1. Copy the web_server folder to your Arduino sketch folder.
2. Copy the UtilityFunctions folder to your Arduino libraries folder.
3. Change the following in the web_server sketch to match your network settings:

const char* ssid = "YOURWIFISSID";
const char* password = "YOURWIFIPASSWORD";
const IPAddress ipadd(192,168,0,132);     
const IPAddress ipgat(192,168,0,1); 

define SVRPORT 9701

4. Server Setting

4.1 To use the standard Arduino Web Server library, which polls for connections, use this define in the sketch:

define SVR_TYPE SVR_HTTP_LIB

4.2 To use the EspressIf SDK Web Server API, which uses event callbacks, use this define in the sketch:

define SVR_TYPE SVR_HTTP_SDK

Operation:

While not necessary, the code assumes an LED is connected to GPIO16. This LED is ON upon 
power-up and is turned OFF once initialization completes.


Web Server test:

Enter the following URL in a web browser (adjust IP & port to your settings):

http://192.168.0.132:9701/?request=GetSensors

A JSON string will be returned with the sensor values in this format:

{
"Ain0":"316.00",
"Ain1":"326.00",
"Ain2":"325.00",
"Ain3":"314.00",
"Ain4":"316.00",
"Ain5":"163.00",
"Ain6":"208.00",
"Ain7":"333.00",
"SYS_Heap":"25408",
"SYS_Time":"26"
}

The server will also respond to requests to turn the LED, if connected, on and off.

To turn on, enter the URL:

http://192.168.0.132:9701/?request=LedOn

To turn off, enter the URL:

http://192.168.0.132:9701/?request=LedOff
