# EV-Communication-System
# IoT based Electric Vehicle Communication System
The purpose is to design lane detection adas feature for electric vehicle and communicate the parameters or factors with the user located at long distance using MQTT protocol.
The lane detection code is taken from https://github.com/canozcivelek/lane-detection-with-steer-and-departure which is mostly dependent on Computer Vision(CV2) library of Python.
Code is taken only for reference to show how we can share the EV data using MQTT protocol easily.
The only change is made is that to communicate this data using MQTT protocol.
MQTT is a pub/sub model. The broker used to communicate data is EMQX. 
Running procedure:
1) Install all the necessary libraries.
2) Run Subscribe Data.py file. You can place this file anywhere as it has no connection with the Lane Detection Publish Data.py file. These two files are connected via broker. You can also send the Subscribe Data.py file to your friend who is at long distance and ask him to run this file. PS. Do not send Lane Detection Publish Data.py file.
3) Run Lane Detection Publish Data.py file, you will find the data on the terminal as well as video will run where lanes are detected (credits are mentioned above). 
Now you will get the data on the terminal where you have run Subscribe Data.py file.
You can also find out various parameters like throughput, data packets captured, packet drop ratio using network analyzer tools like wireshark.
QoS: Quality of Service is decided while publishing and subscribing data. There are 3 QoS in MQTT protocol. 
QoS 0: There is no acknowldgement whether data is received by subscriber or not. Data might be lost in this case.
QoS 1: Data is sent at least once i.e. when there is no acknowledgement from subscriber, publisher keeps on sending data until acknowledgement is received. 
QoS 2: Data is sent at most once i.e. The next data packet is not sent by publisher until acknowledgement is received from subscriber. This QoS uses more system power and it is useful here data plays critical role and data loss is not recommended eg. banks, automation.

For our particular project we are going to use QoS 1 as it is compatible with our project and we want to use system power as low as possible.   
