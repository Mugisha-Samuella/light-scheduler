# IoT Light Scheduler

This project implements a web-based light scheduler using WebSocket and MQTT for the Rwanda Coding Academy's Embedded Systems Software Integration course.

## Features

- Modern, responsive UI with Tailwind CSS
- WebSocket server for receiving schedules
- MQTT integration for time-based light scheduling
- Arduino UNO with relay module for light control

## Setup Instructions

1. **Arduino Setup**:

   - Connect the relay module to Arduino UNO:
     - VCC to 5V, GND to GND, IN to pin 8.
     - Live wire between COM and NO, with insulation.
   - Upload the Arduino code:

     ```cpp
     int relayPin = 8;

     void setup() {
       Serial.begin(9600);
       pinMode(relayPin, OUTPUT);
       digitalWrite(relayPin, HIGH); // Relay OFF initially
     }

     void loop() {
        if (Serial.available() > 0) {
     String cmd = Serial.readStringUntil('\n');
     cmd.trim();
     if (cmd == "ON") {
      digitalWrite(relayPin, LOW); // Relay ON
     } else if (cmd == "OFF") {
      digitalWrite(relayPin, HIGH); // Relay OFF
     }
     }
     }
     ```

## Screenshots

![UI](screenshots/ui.png)

![Server Logs](screenshots/serverlogs.png)

![Subscriber Logs](screenshots/subscriberlogs.png)
