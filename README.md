# Arduino-controlled-turning-light-turns-on-automatically-when-the-sun-goes-down
Arduino-controlled turning light turns on automatically when the sun goes down
// Define LDR pin
#define LDR_PIN A0

// Define LED pin
#define TURNING_LIGHT_PIN 2

// Define threshold value for darkness (adjust as needed)
#define DARKNESS_THRESHOLD 500

void setup() {
  // Initialize serial communication for debugging
  Serial.begin(9600);
  
  // Set LDR pin as input
  pinMode(LDR_PIN, INPUT);
  
  // Set turning light pin as output
  pinMode(TURNING_LIGHT_PIN, OUTPUT);
}

void loop() {
  // Read LDR value
  int ldrValue = analogRead(LDR_PIN);
  
  // Output LDR value for debugging
  Serial.print("LDR Value: ");
  Serial.println(ldrValue);
  
  // Check if it's dark (LDR value below threshold)
  if (ldrValue < DARKNESS_THRESHOLD) {
    // Turn on turning light
    digitalWrite(TURNING_LIGHT_PIN, HIGH);
    Serial.println("Turning Light ON");
  } else {
    // Turn off turning light
    digitalWrite(TURNING_LIGHT_PIN, LOW);
    Serial.println("Turning Light OFF");
  }
  
  // Delay before next reading
  delay(1000); // Adjust delay as needed
}


