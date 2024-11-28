# MQTT Protocol Overview

MQTT (Message Queuing Telemetry Transport) is a lightweight messaging protocol designed for efficient communication between devices, making it ideal for IoT (Internet of Things) applications. It uses a publish/subscribe model to facilitate communication between devices in a network.

## Key Features

### 1. Publish/Subscribe Model
Unlike traditional client-server models, MQTT follows a publish/subscribe paradigm where devices (clients) do not directly communicate with each other. Instead, they interact via a central intermediary called a broker.
![Publish/Subscribe Informal Explanation](https://github.com/user-attachments/assets/271f6887-7506-4f8f-8afc-f241929d8fe4)

- **Publisher**: Sends data (messages) to the broker under a specific topic.
- **Subscriber**: Receives messages from the broker by subscribing to a specific topic.
- **Broker**: Manages message distribution between publishers and subscribers based on topics.
- **Topic**: A hierarchical string (e.g., `home/livingroom/temperature`) used to route messages.

### 2. Lightweight and Efficient Design
MQTT is optimized for low-bandwidth and high-latency networks, making it suitable for devices with limited resources like sensors and embedded systems.

### 3. Quality of Service (QoS) Levels
MQTT QoS is an agreement between the message sender and receiver that defines the level of delivery guarantee for a specific message. MQTT offers three levels of QoS to ensure reliable message delivery:

#### **QoS 0**: At most once (no acknowledgment).
- It is called as `Fire and Forget level`, messages are sent without any confirmation from the receiver.
- This means it is technically possible for a message to get lost, given an unreliable connection.
![QoS Level 0](https://github.com/user-attachments/assets/e5fe46a6-855c-4e83-a250-9e205f46361c)

#### **QoS 1**: At least once (acknowledged delivery).
- In QoS level 1, the receiver must send a confirmation **(PUBACK)** to let the sender know that the message was received.
- However, it is possible that the receiver gets a message multiple times.
- This QoS level ensures that a message makes it from sender to receiver but doesn't ensure that it received exactly once.
![QoS level 1](https://github.com/user-attachments/assets/78073a35-7253-4a24-84e4-03cd88e415da)

#### **QoS 2**: Exactly once (ensures no duplicates).
It uses a four-step communication process to ensure the message is sent exactly once only. It offers the highest level of QoS in MQTT ensuring the message is delivered once through four-step handshake between the sender and receiver.
- When a receiver gets a QoS 2 PUBLISH packet from a sender it replies to sender with a `PUBREC` packet that acknowledges the publisher.
- If the sender doesn't get the `PUBREC` packet from the receiver, it sends the packet again with a duplicate flag known as `PUBREL` until it receives an acknowledgement.
![image](https://github.com/user-attachments/assets/d87c4859-8f1a-4345-8830-f008c75e8953)

#### **Summary for the QoS levels**
![QoS Levels](https://github.com/user-attachments/assets/3aa82c10-af7c-4634-ba6a-9ce24522b5f3)

### 4. Bidirectional Communication Protocol
- This means a device can be a publisher and a subscriber at the same time.
- This also allows easy broadcasting of messages to several devices at once.

### 5. Security 
- MQTT makes it easy to encrypt messages through the broker and the other users also.
- The standard unsecured port is 1883.
- The default secured MQTT broker port is 8883.
- The use of ACLs (Access Control Lists) allows restriction of subscriptions and publishing of clients.

## How MQTT Works
1. A publisher sends a message to the broker under a specific topic (e.g., `home/kitchen/temperature`).
2. The broker forwards the message to all subscribers who have subscribed to that topic.
3. Subscribers receive the message in real-time if they are connected to the broker.

## Example Use Cases

### Example 1: Smart Home Temperature Monitoring
- **Publisher**: A temperature sensor publishes readings to the topic `home/livingroom/temperature`.
- **Broker**: Receives the temperature data and forwards it to subscribers.
- **Subscriber**: A mobile app subscribed to `home/livingroom/temperature` displays the real-time temperature.

# Example 2: Controlling a Smart Light

- **Publisher**: A mobile app sends a command to `home/livingroom/light` (e.g., ON or OFF).  
- **Broker**: Forward the command to the subscribed light device.  
- **Subscriber**: The smart light turns on or off based on the received command.  

Also, Here you can see an application for what is special in MQTT "Bidirectional Communication Protocol". After the light device is turned on or off, we can initiate another way of communication fo acknowledgement.

- **Subscriber**: The smart light sends its status after the command under the same topic 
- **Broker**: Forward the command to the subscribed mobile device.  
- **Subscriber**: The mobile app received a piece of information about the smart light's status after the command.
![Smart Light System using MQTT](https://github.com/user-attachments/assets/9d429505-91b3-4687-b167-ade36c6f43fe)


## Examples for the MQTT Brokers

# References
- [MQTT-The Standard for IOT Messaging](https://youtu.be/fbf7SoFVjP4?si=bHV7psqcgI7gRpFe)
- [What is MQTT Quality of Service (QoS) 0,1, & 2? – MQTT Essentials](https://www.hivemq.com/blog/mqtt-essentials-part-6-mqtt-quality-of-service-levels/) 
