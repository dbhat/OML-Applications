OML-Applications
================

This application converts a CSV-formatted file to OML Measurement Points to be displayed on a live-graph in LabWiki.

The example here is written for an application that measures the signal strength (among other parameters of interest) from a cellular phone for different service providers including Wimax.

### The sample CSV file:
<pre><code>
"1401394008","6C:F3:73:99:FA:1E","samsung","SPH-D710","Android","EVDO Rev 0","Sprint","99.207.13.249",-96,,"-82.8344","34.676","23.517"
"1401393251","f8:a9:d0:66:7d:78","LGE","LG-D801","Android","Wifi",,"198.21.252.5",-81,"eduroam","-82.8344","34.676","25.854"
"1401392753","6C:F3:73:99:FA:1E","samsung","SPH-D710","Android","EVDO Rev 0","Sprint","99.207.13.249",-96,,"-82.8344","34.676","17.06"
"1401392748","6C:F3:73:99:FA:1E","samsung","SPH-D710","Android","EVDO Rev 0","Sprint","99.207.13.249",-96,,"-82.8344","34.676","24.803"
"1401392619","6C:F3:73:99:FA:1E","samsung","SPH-D710","Android","EVDO Rev 0","Sprint","99.207.13.249",-101,,"-82.8344","34.676","20"
"1401392598","6C:F3:73:99:FA:1E","samsung","SPH-D710","Android","EVDO Rev 0","Sprint","99.207.13.249",-96,,"-82.8344","34.676","21.088"
</code></pre>
### Explanation of the above fields in order of appearance, separated by ','
<pre><code>
a) testTime: Timestamp of when the test was initiated in unix timestamp
b) mac: We use this to uniquely identify the devices. It is the MAC
address of the Wifi interface of a device.
b) make: Device manufacturer
c) model: Device model
d) platform: Operating system
e) networkType: Radio access technology
f) networkOperator: Cell network operator (null for Wifi tests)
g) ipAddress: IP that the server saw during the test
h) signalDbm: signal dBm as reported by the device's radio
i) ssid: SSID of the wifi network used (null for cell tests)
j) longitude: longitude of current location
k) latitude: latitude of current location
l) geolocationAccuracy: precision of location data in meters
</code></pre>

The application uses the File-tail gem (Link: https://github.com/flori/file-tail) to continuously tail the CSV file and the OML4r gem (Link: https://github.com/mytestbed/oml4r) to convert the fields to Measurement Points.

wimaxss_app.rb - The OML4r application defnition.
wimaxss.oedl - The OEDL script for LabWiki. The path of the file and location of application script are variable parameters.

