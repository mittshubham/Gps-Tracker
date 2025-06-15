#include <SoftwareSerial.h>
#define a 7  // Button for SMS
#define b 8  // Button for Call

SoftwareSerial a9gSerial(2, 3); // RX, TX for A9G communication

void setup() {
  // Set button pins as input
  pinMode(a, INPUT);
  pinMode(b, INPUT);
  
  // Initialize Serial Monitor
  Serial.begin(9600);

  // Initialize A9G serial communication
  a9gSerial.begin(9600);

  delay(2000);
  Serial.println("A9G Module Initialized");
}

void loop() {
  // Check if the button for SMS (pin 7) is pressed
  if (digitalRead(a) == HIGH) {
    Serial.println("Sending SMS...");

    // Set SMS mode to text
    a9gSerial.println("AT+CMGF=1");
    delay(1000);
    
    // Send the phone number
    a9gSerial.println("AT+CMGS=\"+919307271596\""); 
    delay(1000);

    // Wait for '>' prompt (simulated with a delay here)
    // Ideally, you would read the response and wait until '>' is received
    delay(1000);
    
    // Send the message text
    a9gSerial.println("Hello, This is a test message"); 
    delay(1000);

    // End the message with Ctrl+Z (ASCII 26)
    a9gSerial.write(26);
    delay(1000);

    Serial.println("Message sent!");
  }

  // Check if the button for Call (pin 8) is pressed
  if (digitalRead(b) == HIGH) {
    Serial.println("Calling...");
    
    // Dial the phone number
    a9gSerial.println("ATD+919307271596;");  // Add semicolon to dial
    delay(1000);

    Serial.println("Call sent!");
  }
}
