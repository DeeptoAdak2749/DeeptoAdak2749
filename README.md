int waterPump = 10;
int redWaterLed = 13;
int greenWaterLed = 12;
int greenLed = 11;
int yellowLed = 9;
int redLed = 8;


void setup() {
  Serial.begin(9600);
  pinMode(waterPump, OUTPUT);
  pinMode(2, OUTPUT);
  digitalWrite(2, HIGH);
  pinMode(3, OUTPUT);
  digitalWrite(3, HIGH);
  pinMode(7, OUTPUT);
  digitalWrite(7, HIGH);
}
 
void loop() {
  int value = analogRead(A0);
  int pot  = analogRead(A1);
  int potValue = pot;
  Serial.println(value);
  Serial.println(potValue);
  delay(1000);
  if (value > potValue) {
    digitalWrite(waterPump, HIGH);
    digitalWrite(greenWaterLed, HIGH);
    digitalWrite(redWaterLed, LOW);
    delay(6000);
    digitalWrite(waterPump, LOW);
    digitalWrite(greenWaterLed, LOW);
    digitalWrite(redWaterLed, HIGH);
  } else {
    digitalWrite(waterPump, LOW);
    digitalWrite(redWaterLed, HIGH);

  }
 
  if (value < 300) {
    digitalWrite(greenLed, HIGH);
    digitalWrite(redLed, LOW);
    digitalWrite(yellowLed, LOW);
  } 
  else if (value > 300 && value < 950) {
    digitalWrite(yellowLed, HIGH);
    digitalWrite(redLed, LOW);
    digitalWrite(greenLed, LOW);
  } 
  else if (value > 950) {
    digitalWrite(redLed, HIGH);
    digitalWrite(greenLed, LOW);
    digitalWrite(yellowLed, LOW);
  }
}
