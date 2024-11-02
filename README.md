<img width="1280" alt="readme-banner" src="https://github.com/user-attachments/assets/35332e92-44cb-425b-9dff-27bcf1023c6c">

# Chatterleaf 🌿


## Basic Details
### Team Name: Ohmies


### Team Members
- Team Lead: Aiswarya Chandrasekharan - Toc H Institute of Science and Technology
- Member 2: Bhavana V Nair - Toc H Institute of Science and Technology
- Member 3: Hansel Sabu - Toc H Institute of Science and Technology

### Project Description
This is an IoT based agricultural automation project which focus on plant monitoring system. It measures the temperature and humidity of the atmosphere providing real time values which helps the plant moms/dads to know about the situations which their plant goes through. It can be extended to agricultural  sector as well. But the primary aim is to understand the various moods of plant based on the moisture level of the soil. Thus the plant moms/dads will know what their child goes through. Since plant cannot be watered the same everyday , it requires to be watered when it needs . Thus the plant watering is automated so that the plant is happy.
### The Problem (that doesn't exist)
Justice for the Unspoken.

### The Solution (that nobody asked for)
Giving the unspoken "the voice"

## Technical Details
### Technologies/Components Used
For Software:
- Embedded C
- Arduino IDE
- WiFi,Esp 32, Temperature and Moisture
- Blynk 

For Hardware:
- Esp 32,Temperature and humidity sensor, moisture sensor, pump,Motor Driver, Battery, Breadboard,Wires
- Esp 32 DevKitV1,DHT11, L298N Driver, 9V Battery

### Implementation
For Software: #define BLYNK_TEMPLATE_ID "TMPL3gTw2LNyQ"
#define BLYNK_TEMPLATE_NAME "agriculture using esp32"
#define BLYNK_AUTH_TOKEN "IUktBWJeBqTkAaGR-D-p5yhEYejA0kzJ"
#include <WiFi.h>
#include <BlynkSimpleEsp32.h>
#include <DHT.h>


// WiFi credentials
char ssid[] = "SSID";
char pass[] = "Password";


// Blynk authentication token
char auth[] = "IUktBWJeBqTkAaGR-D-p5yhEYejA0kzJ";




// DHT sensor configuration
#define DHT_PIN 4   // GPIO pin connected to DHT sensor
#define DHT_TYPE DHT11
#define SOIL_MOISTURE_PIN 32
#define PUMP_PIN 14
DHT dht(DHT_PIN, DHT_TYPE);


void setup() {
  Serial.begin(9600);


  // Connect to WiFi
  WiFi.begin(ssid, pass);
  while (WiFi.status() != WL_CONNECTED) {
    delay(250);
    Serial.print(".");
  }
  Serial.println("\nConnected to WiFi");


  // Initialize Blynk
  Blynk.begin(auth, ssid, pass);
  // Initialize DHT sensor
  dht.begin();


  // Set motor pins and pump pin as outputs
  pinMode(PUMP_PIN, OUTPUT);
}


void loop() {
  Blynk.run();
  Blynk.run();


  // Read temperature, humidity, and soil moisture
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();
  float soil_moisture = analogRead(SOIL_MOISTURE_PIN);


  // Display data on Blynk app
  Blynk.virtualWrite(V0, temperature);
  Blynk.virtualWrite(V1, humidity);
  Blynk.virtualWrite(V2, soil_moisture);


  // Check soil moisture level and turn on pump if below threshold
  if (soil_moisture >4000) {
    Blynk.logEvent("agriculture_using_esp32"); // Adjust threshold value as needed
    digitalWrite(PUMP_PIN, HIGH); // Turn on the pump
    delay(2000); // Pump runs for 2 seconds
    digitalWrite(PUMP_PIN, LOW); // Turn off the pump
  } else {
   
    digitalWrite(PUMP_PIN, LOW); // Turn off the pump
    // Rotate the motor based on Blynk input
    Blynk.run();
  }

}
### Project Documentation
For Software:

# Screenshots (Add at least 3)
![Screenshot1](Add screenshot 1 here with proper name)
*Add caption explaining what this shows*

![Screenshot2](Add screenshot 2 here with proper name)
*Add caption explaining what this shows*

![Screenshot3](Add screenshot 3 here with proper name)
*Add caption explaining what this shows*

# Diagrams
![Workflow](Add your workflow/architecture diagram here)
*Add caption explaining your workflow*

For Hardware:

# Schematic & Circuit
![Circuit](Add your circuit diagram here)
*Add caption explaining connections*

![Schematic](Add your schematic diagram here)
*Add caption explaining the schematic*

# Build Photos
![Components](Add photo of your components here)
*List out all components shown*

![Build](Add photos of build process here)
*Explain the build steps*

![Final](Add photo of final product here)
*Explain the final build*

### Project Demo
# Video
[Add your demo video link here]
*Explain what the video demonstrates*

# Additional Demos
[Add any extra demo materials/links]

## Team Contributions
- [Name 1]: [Specific contributions]
- [Name 2]: [Specific contributions]
- [Name 3]: [Specific contributions]

---
Made with ❤️ at TinkerHub Useless Projects 

![Static Badge](https://img.shields.io/badge/TinkerHub-24?color=%23000000&link=https%3A%2F%2Fwww.tinkerhub.org%2F)
![Static Badge](https://img.shields.io/badge/UselessProject--24-24?link=https%3A%2F%2Fwww.tinkerhub.org%2Fevents%2FQ2Q1TQKX6Q%2FUseless%2520Projects)



