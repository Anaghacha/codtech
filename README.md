# codtech
This repository consists of the 4 tasks that were to be done for INTERNET OF THINGS :
COMPANY : CODTECH IT SOLUTIONS 
NAME :ANAGHA CHALLA
INTERN ID : CT12GDM
DOMAIN : INTERNET OF THINGS 
DURATION : 8 WEEKS 
MENTOR:Neela Santhosh Kumar


# TASK 1 :SMART LIGHT CONTROL 

This project allows you to control an LED connected to an Arduino board using Serial Monitor commands. You can turn the LED **ON** or **OFF** by entering commands through the Arduino Serial Monitor.

## Components Required
- Arduino Board (Uno, Mega, Nano, etc.)
- LED
- 220Ω Resistor
- Jumper Wires

## Circuit Diagram
1. Connect the **anode** (longer leg) of the LED to **pin 9** on the Arduino.
2. Connect the **cathode** (shorter leg) to **GND** through a **220Ω resistor**.

## Installation & Usage
1. **Upload the Code**:  
   - Open the Arduino IDE.
   - Copy and paste the code below into the **Arduino IDE**.
   - Select the correct **Board** and **Port**.
   - Click **Upload**.

2. **Open Serial Monitor**:  
   - Set the baud rate to **9600**.
   - Enter **"ON"** to turn the LED on.
   - Enter **"OFF"** to turn the LED off.

## Code
```cpp
#define LED_PIN 9  // LED connected to pin 9

void setup() {
    Serial.begin(9600);  // Start Serial Communication
    pinMode(LED_PIN, OUTPUT);
    Serial.println("Enter 'ON' to turn on LED, 'OFF' to turn it off");
}

void loop() {
    if (Serial.available()) {
        String command = Serial.readStringUntil('\n');  // Read Serial Input
        command.trim();  // Remove any extra spaces or newlines
        
        if (command == "ON") {
            digitalWrite(LED_PIN, HIGH);
            Serial.println("LED Turned ON");
        } 
        else if (command == "OFF") {
            digitalWrite(LED_PIN, LOW);
            Serial.println("LED Turned OFF");
        } 
        else {
            Serial.println("Invalid Command. Use 'ON' or 'OFF'");
        }
    }
}

#TASK 2 :HOME AUTOMATION SYSTEM
IR Remote-Controlled Home Automation System

Overview

This project implements a home automation system using an Arduino, an IR receiver, and an LCD display. The system allows users to control appliances such as a TV, light, fan, and motor using an IR remote.

Components Used

Arduino Uno: Microcontroller to process IR signals and control appliances

IR Receiver: Receives signals from the remote

IR Remote Control: Sends commands to the system

16x2 LCD Display: Displays system status

Relay Module: Controls high-voltage appliances

LEDs: Simulate appliances

Buzzer: Provides audio feedback

Resistors and Jumper Wires: For circuit connections

Power Supply: Powers the Arduino and components

Features

Control appliances using an IR remote

LCD display for real-time status updates

Buzzer feedback for button presses

Expandable to support additional devices

Circuit Diagram

The circuit consists of:

The IR receiver connected to the Arduino.

The LCD display interfaced with the Arduino.

Relays to control appliances.

LEDs used to simulate real appliances.

Installation and Setup

Wiring: Connect components as per the circuit diagram.

Upload Code: Flash the Arduino sketch using the Arduino IDE.

Test System: Use the IR remote to control appliances.

Usage Instructions

Press the corresponding buttons on the IR remote to turn devices ON/OFF.

The LCD displays the current status of each device.

The buzzer sounds when a command is received.

Future Improvements

Integrating Wi-Fi or Bluetooth for smartphone control.

Adding voice control using AI assistants.

Expanding to control more appliances.

License

This project is open-source and can be modified and shared freely.
# TASK 3 : IOT SECURITY SYSTEM
This project uses a **PIR motion sensor** to detect motion. When motion is detected, an LED turns on, a buzzer sounds, and a message is displayed on the **Serial Monitor**.

## Components Required
- Arduino Board (Uno, Mega, Nano, etc.)
- PIR Motion Sensor
- LED
- 220Ω Resistor
- Buzzer
- Jumper Wires

## Circuit Diagram
1. **PIR Sensor**  
   - **VCC** → **5V** on Arduino  
   - **GND** → **GND** on Arduino  
   - **OUT** → **Pin 8** on Arduino  

2. **LED**  
   - **Anode (long leg)** → **Pin 9** via a **220Ω resistor**  
   - **Cathode (short leg)** → **GND**  

3. **Buzzer**  
   - **Positive (+)** → **Pin 10**  
   - **Negative (-)** → **GND**  

## Installation & Usage
1. **Upload the Code**  
   - Open the Arduino IDE.  
   - Copy and paste the code below into the **Arduino IDE**.  
   - Select the correct **Board** and **Port**.  
   - Click **Upload**.  

2. **Open Serial Monitor**  
   - Set the baud rate to **9600**.  
   - When motion is detected, the LED will turn on, and the buzzer will sound.  
   - The Serial Monitor will display **"Motion detected!"**.  
   - When motion stops, the Serial Monitor will display **"Motion stopped!"**.  

## Code
```cpp
int led = 9;
int sensor = 8;
int buzzer = 10;
int state = LOW;
int val = 0;

void setup()
{
  pinMode(led, OUTPUT);
  pinMode(sensor, INPUT);
  pinMode(buzzer, OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  val = digitalRead(sensor);
  if (val == HIGH)
  {
    // check if the sensor is HIGH
    digitalWrite(led, HIGH);
    delay(100);
    if (state == LOW)
    {
      Serial.println("Motion detected!");
      tone(buzzer, 1000);
      state = HIGH;
    }
  }
  else
  {
    digitalWrite(led, LOW);
    delay(200);
    if (state == HIGH)
    {
      Serial.println("Motion stopped!");
      noTone(buzzer);
      state = LOW;
    }
  }
}

#  TASK 4 :IoT Air Quality Monitor 🚀

This repository contains the **IoT Air Quality Monitoring System** using **Arduino, ESP8266, and an LCD display** to measure and transmit air quality data.

---

## **Project Overview**
This project monitors **air quality** using an **analog sensor** and displays the data on an **LCD screen** while sending it to the cloud using **ESP8266 Wi-Fi module**.

### **Key Features**
✅ **Air Quality Monitoring** – Reads sensor values and determines air quality levels.  
✅ **LCD Display** – Shows real-time air quality in **PPM (Parts Per Million)**.  
✅ **Cloud Integration** – Sends data to **ThingSpeak** for remote monitoring.  
✅ **Wi-Fi Connectivity** – Uses **ESP8266** for seamless cloud updates.  
✅ **Smart Alerts** – Displays **Fresh Air, Poor Air, or Very Poor** based on air quality levels.  

---

## **Hardware Requirements**
- **Arduino Board**
- **ESP8266 Wi-Fi Module**
- **16x2 LCD Display**
- **Air Quality Sensor (Analog Input)**
- **Resistors & Wires for connections**
- **Power Supply (5V)**

---

## **Circuit Connections**
| **Component** | **Pin Connection** |
|--------------|------------------|
| **LCD RS** | Arduino **D13** |
| **LCD Enable** | Arduino **D12** |
| **LCD D4-D7** | Arduino **D6, D5, D4, D3** |
| **LCD R/W** | **Ground (GND)** |
| **LCD VCC** | **5V** |
| **ESP8266 TX** | Arduino **D9** |
| **ESP8266 RX** | Arduino **D8** |
| **Air Quality Sensor** | Arduino **A0** |

---

## **How It Works**
1. **Initialization** – The system starts with a **Welcome message** on the LCD.  
2. **Wi-Fi Connection** – The ESP8266 connects to a **Wi-Fi network**.  
3. **Sensor Reading** – The analog sensor reads **air quality levels**.  
4. **Data Display** – The LCD shows **PPM value** and air quality status:
   - **Fresh Air** (PPM ≤ 500)  
   - **Poor Air** (500 < PPM ≤ 1000)  
   - **Very Poor** (PPM > 1000)  
5. **Cloud Upload** – Sensor data is uploaded to **ThingSpeak** for remote access.

---

## **Code Setup**
### **1. Clone the Repository**
```bash
git clone https://github.com/your-username/IoT-Air-Quality-Monitor.git

