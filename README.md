# ESP32 Projects on Wokwi

This repository contains four ESP32 example projects created and simulated using the [Wokwi](https://wokwi.com/) platform. Each project demonstrates a fundamental concept of working with ESP32 microcontrollers.

## Examples

### 1. Blinking LED  
This example demonstrates how to blink an LED connected to the ESP32.  
- **Purpose:** Learn how to use GPIO pins to control an LED.  
- **Simulation Link:** [Blinking LED](https://wokwi.com/projects/415807653405498369)  

### 2. Reading Analog Value of a Potentiometer  
This example shows how to read the analog value of a potentiometer using the ADC (Analog-to-Digital Converter) on the ESP32.  
- **Purpose:** Understand how to interface analog sensors with ESP32.  
- **Simulation Link:** [Read Analog Value of Potentiometer](https://wokwi.com/projects/415812356140451841)  

### 3. Temperature Sensor Reading  
This example demonstrates how to read data from a temperature sensor connected to the ESP32.  
- **Purpose:** Learn how to interface a sensor and process its data.  
- **Simulation Link:** [Temperature Sensor Reading](https://wokwi.com/projects/415815447237870593)  

## MQTT Explanation

### What is MQTT?
MQTT (Message Queuing Telemetry Transport) is a lightweight and open-source messaging protocol designed for efficient communication between devices in IoT (Internet of Things) applications. It is particularly well-suited for scenarios where network bandwidth is limited or when devices need to operate with minimal power.

### Key Features of MQTT
- **Publish/Subscribe Model:** Devices can publish data to a topic or subscribe to receive data from a topic, enabling one-to-many communication.
- **Low Bandwidth Usage:** MQTT's small message overhead makes it ideal for low-bandwidth environments.
- **Quality of Service (QoS) Levels:** Offers three QoS levels for message delivery: 
  - **QoS 0**: "At most once" delivery.
  - **QoS 1**: "At least once" delivery with acknowledgment.
  - **QoS 2**: "Exactly once" delivery with a four-step handshake.

### MQTT Broker: Mosquitto
- **Mosquitto** is an open-source MQTT broker that facilitates communication between devices using the MQTT protocol. It can handle message routing between different clients and is commonly used in IoT applications.
- **Installation:** Mosquitto can be installed on various platforms, such as Windows, Linux, and macOS. It provides reliable message delivery and supports both MQTT and MQTT over WebSockets.
- **How It Works:** The ESP32 client connects to the Mosquitto broker, publishes data to a specific topic, and subscribes to receive data from other topics. The broker handles message distribution to all relevant subscribers.

## Tools and Requirements
- [Wokwi](https://wokwi.com/) online simulator  
- MQTT broker (e.g., [Mosquitto](https://mosquitto.org/))  
- Basic understanding of ESP32 GPIO, ADC functionality, and networking concepts
