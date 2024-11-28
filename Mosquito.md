# Mosquito Broker
Mosquitto is a popular and open-source message broker that implements the MQTT protocol.
- In the world of IoT, where devices need to communicate efficiently, Mosq##uitto’s ability to handle multiple connections and deliver messages in real-time is very useful.
- Mosquitto MQTT can run on various operating systems, including Linux, Windows, macOS, and even on Raspberry Pi.
![Mosquitto MQTT](https://github.com/user-attachments/assets/fa2c3f1b-6066-4f54-bcd8-bc1dad0b3165)

## Installation 
1- Download the broker from ![here](https://drive.google.com/file/d/1SD-kV9AA8u5YRWwkjpYQbh_VABFwUCq9/view?usp=drive_link)
2- Install the file there through click `Next` till the end.
3- Don't forget to know the installed file path

## Network Configuration
1- Open the installed file path.
2- Create a text file named test.conf under the Mosquitto folder (C:\Program Files\mosquitto).
3- Open the created file, and write the following commands:
    ```
    listener 1883
    allow_anonymous true  
    ```
4- change the directory using this code
    ```
    cd C:\Program Files\mosquitto
    mosquitto -c test.conf -v
    ```
    ▪ -c test.conf: Specifies a configuration file for the Mosquitto broker.
    ▪ -v: Enables verbose mode to provide additional information and logging.
5- For Getting Broker IP: Open CMD window and write `ipconfig` to get the broker IP.

We will use Python Client to operate the network we need in MQTT. We will install `The Paho Python Client` provides a client class with support for MQTT.

6- Add this command in the CMD
    ```
    pip install paho-mqtt==1.6.1
    ```
![MQTT Model](https://github.com/user-attachments/assets/bc065b7c-3fc4-4ef1-a8a9-d0b3a1d921a4)

7- Operate the Publisher Code
```python
# Import the necessary modules
import paho.mqtt.client as mqtt
from time import sleep

# MQTT broker address
broker_ip = "192.168.137.1"

# MQTT broker port
port = 1883

# MQTT topic to which the publisher will publish messages
topic = "home/led"

# Quality of Service (QoS)
qos = 0

# Create an MQTT client instance with the name "publisher"
client = mqtt.Client("publisher")

# Connect to the MQTT broker using the specified IP address and port
client.connect(broker_ip, port)

# Infinite loop to continuously publish messages
while True:
    # Message to be published
    message = "Turn On"

    # Publish the message to the specified topic
    client.publish(topic, message, qos)

    # Print a message indicating that the message has been published
    print("Published message:", message)

    # Wait for 2 seconds before publishing the next message
    sleep(2)

# Disconnect from the MQTT broker
client.disconnect()
```
