# Smart-water-management-for-rajsthan
This repository showcases Rajasthan’s smart water management initiatives, including MJSA, Jal Shakti Abhiyan, and ADB-supported projects. It features data on water conservation, SCADA monitoring, and community engagement, serving as a resource for policymakers, researchers, and development partners." Let me know if you'd like a version tailored .
🧩 Problem Statement
"Rajasthan faces acute water scarcity due to low rainfall and high evaporation. To ensure efficient water usage and reduce wastage, a smart water management system is needed that monitors water levels in tanks and reservoirs, automates irrigation, and provides real-time data to authorities and users."

💻 Code Format: Arduino-Based Smart Water Level Monitoring
This sample code uses an ultrasonic sensor to detect water level and a solenoid valve to control water flow.


#define trigPin 9
#define echoPin 10
#define valvePin 8

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(valvePin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  Serial.print("Water Level (cm): ");
  Serial.println(distance);

  if (distance < 10) {
    digitalWrite(valvePin, LOW); // Close valve
    Serial.println("Tank Full - Valve Closed");
  } else {
    digitalWrite(valvePin, HIGH); // Open valve
    Serial.println("Tank Not Full - Valve Open");
  }

  delay(1000);
}
