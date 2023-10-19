# SmartHomeIOT







Smart Home Automation  Project

Created by (Name, Details)
Table of Contents
Created by (Name, Details)	1
Overview	3
Requirements & Components Used	3
The Circuit Design	3
The components were connected as given below	3
The Program Excution Code	4
C Program	4
For Python	5
Other Services Used	5
Simulation	6

Overview

We creating  smart home IoT Device with Arduino in Wokwi Simulator In this project, we'll create a simple simulation of a smart home system that includes a temperature sensor and a relay-controlled lamp. 

Requirements & Components Used

In this project, we have used the following components

    • Arduino Uno
    • DHT22 Temperature Sensor (for simulating temperature data)
    • Relay Module (for controlling a lamp)
    • LED (to represent the lamp)
    • Breadboard and wires to connect the components
      

The Circuit Design
The components were connected as given below

    • We connected the VCC and GND pins of the DHT22 to the 5V and GND on the Arduino.
    • 
    • We connected the data pin of the DHT22 to any digital pin on the Arduino (e.g., pin 2).
    • 
    • We connected one end of the relay module to a digital pin on the Arduino (e.g., pin 3) and the other end to GND.
    • 
    • We connected one leg of the LED to the NO (Normally Open) terminal of the relay module.
    • 
    • We connected the other leg of the LED to a current-limiting resistor (330-470 ohms) and then to the 5V on the Arduino.


The Program Excution Code

C Program

#include <Adafruit_Sensor.h>
#include <DHT.h>	
#include <DHT_U.h>

#define DHTPIN 2       // DHT22 data pin
#define DHTTYPE DHT22  // DHT22 sensor type
#define RELAY_PIN 3    // Pin connected to the relay module

DHT_Unified dht(DHTPIN, DHTTYPE);
float temperature = 0.0;

void setup() {
  dht.begin();
  pinMode(RELAY_PIN, OUTPUT);
  digitalWrite(RELAY_PIN, LOW);  // Turn off the relay initially
}

void loop() {
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  temperature = event.temperature;

  // Check the temperature and control the lamp
  if (temperature >= 25.0) {
    digitalWrite(RELAY_PIN, HIGH); // Turn on the lamp
  } else {
    digitalWrite(RELAY_PIN, LOW);  // Turn off the lamp
  }
  delay(2000); // Delay for 2 seconds
}



For Python
import Adafruit_DHT

DHTPIN = 2       # DHT22 data pin
DHTTYPE = Adafruit_DHT.DHT22  # DHT22 sensor type
RELAY_PIN = 3    # Pin connected to the relay module

dht = Adafruit_DHT.DHT22(DHTPIN)
temperature = 0.0

def setup():
    dht.begin()
    GPIO.setup(RELAY_PIN, GPIO.OUT)
    GPIO.output(RELAY_PIN, GPIO.LOW)  # Turn off the relay initially

def loop():
    humidity, temperature = Adafruit_DHT.read_retry(DHTTYPE, DHTPIN)
    # Check the temperature and control the lamp
    if temperature >= 25.0:
        GPIO.output(RELAY_PIN, GPIO.HIGH)  # Turn on the lamp
    else:
        GPIO.output(RELAY_PIN, GPIO.LOW)  # Turn off the lamp
    time.sleep(2)  # Delay for 2 seconds
**Step 6: Upload the Code**

Copy and paste the code into the Arduino IDE within the Wokwi platform. Then, click the "Upload" button to program the Arduino.

Other Services Used
We have used Blynk IoT Management Platform to ensure that we can control the IoT device remotely
We have also successfully implemented with Firebase
We have used the MQTT protocol and for which we used HiveMQ protocol broker
We have a created and android app using the MIT appinventor 2
Simulation

Once the code is uploaded, and we run the simulation. We observe how the temperature sensor data affects the lamp (LED) based on the defined threshold (25.0°C in this example).

