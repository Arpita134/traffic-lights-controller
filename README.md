# traffic-lights-controller
The goal of this project is to simulate a simple yet effective traffic light system using an Arduino Uno microcontroller, three LEDs (Red, Yellow, Green), and a push button for pedestrian crossing. This project provides a hands-on experience for 1st and 2nd-year students, helping them understand the basics of electronics, coding, and traffic management.
Working of the Basic Traffic Light System:
feature:
Power On:

When the system is powered on, the Arduino initializes the LED pins (red, yellow, green) as outputs and the button pin as an input.

Normal Cycle:

Green Light: The system starts with the green LED turned on for 5 seconds, allowing cars to pass.

Yellow Light: After the green light, the yellow LED is turned on for 2 seconds, signaling drivers to prepare to stop.

Red Light: Then, the red LED is turned on for 5 seconds, stopping all cars. The cycle then repeats.

Pedestrian Crossing:

Button Press: When the pedestrian push button is pressed, the system immediately switches to the red LED, stopping all cars to allow pedestrians to cross safely.

The red light remains on for 5 seconds during pedestrian crossing, after which the system resumes its normal cycle.
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


