
const int redLED = 10;
const int yellowLED = 9;
const int greenLED = 8;
const int button = 7;
int buttonState = 0;

void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(button, INPUT);
}

void loop() {
  buttonState = digitalRead(button);
  
  if (buttonState == HIGH) {
    digitalWrite(greenLED, LOW);
    digitalWrite(yellowLED, LOW);
    digitalWrite(redLED, HIGH);
    delay(5000); // wait for 5 seconds
  } else {
    digitalWrite(greenLED, HIGH);
    delay(5000); // green light on for 5 seconds
    digitalWrite(greenLED, LOW);
    digitalWrite(yellowLED, HIGH);
    delay(2000); // yellow light on for 2 seconds
    digitalWrite(yellowLED, LOW);
    digitalWrite(redLED, HIGH);
    delay(5000); // red light on for 5 seconds
    digitalWrite(redLED, LOW);
  }
}


