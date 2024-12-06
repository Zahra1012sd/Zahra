# Zahra
#define TRIG_PIN 9
#define ECHO_PIN 10
#define SENSOR_HEIGHT 200  
void setup() {
  Serial.begin(9600);  
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
}

void loop() {
  long duration;
  float distanceFromHead;
  float personHeight;
  

  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  

  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);
  

  duration = pulseIn(ECHO_PIN, HIGH);
  

  distanceFromHead = (duration * 0.034) / 2;
  
  
  personHeight = SENSOR_HEIGHT - distanceFromHead;
  
  
  Serial.print("Person Height: ");
  Serial.print(personHeight);
  Serial.println(" cm");
  
  delay(1000);  
}
