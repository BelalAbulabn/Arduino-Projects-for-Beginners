
# Simple Servo Control with a Potentiometer Using Arduino

## Introduction

In this tutorial, you’ll learn how to control a servo motor’s position by turning a potentiometer knob. The servo will rotate between 0° and 180° depending on the potentiometer’s input reading. This hands-on project helps beginners understand how to:

- Read an analog input from a potentiometer.
- Map the input value to a servo’s angle.
- Use an Arduino to smoothly control a servo motor.

## Prerequisites

- **Internet Access**: We’ll use the Wokwi Arduino Simulator.
- **Modern Web Browser**: Chrome, Firefox, or similar.
- **Basic Arduino Familiarity**: Helpful but not required.

## Section One: Setting Up the Wokwi Environment

### Step 1: Create a New Project

1. Go to [Wokwi Arduino Simulator](https://wokwi.com/).
2. Click on **"Start Creating"** or go directly to [New Arduino Uno Project](https://wokwi.com/projects/new/arduino-uno).

**Illustration:**
![Wokwi New Project Button](https://i.imgur.com/lJZFm53.png)

### Step 2: Adding Components

- **Arduino Uno**: Provided by default.

**Servo Motor:**
1. Click on **"Parts"** in the left sidebar.
2. Search for **"Servo"**.
3. Drag and drop the **Servo** onto the workspace.

**Potentiometer:**
1. Search for **"Potentiometer"** or **"Rotary Pot"**.
2. Drag and drop it onto the workspace.

**Illustration:**
![Adding Servo and Potentiometer](https://i.imgur.com/VaaFgSN.png)

## Section Two: Wiring the Components

### Step 1: Servo Motor Wiring

Servos typically have three wires:
- Brown/Black: Ground (GND)
- Red: Power (5V)
- Orange/Yellow: Signal (Control pin)

**Connection Steps:**
1. Connect the servo’s **Ground (Brown/Black)** to the Arduino’s **GND** pin.
2. Connect the servo’s **5V (Red)** to the Arduino’s **5V** pin.
3. Connect the servo’s **Signal (Orange/Yellow)** to **Arduino Digital Pin 9**.

**Illustration:**
![Servo Wiring](https://i.imgur.com/KQcd9aH.png)  
*Sample illustration of connecting the servo wires to Arduino.*

### Step 2: Potentiometer Wiring

A typical potentiometer has three terminals:
- Left Terminal: Connect to **5V**.
- Right Terminal: Connect to **GND**.
- Middle (Wiper): Output signal that goes to an Arduino analog input pin.

**Connection Steps:**
1. Connect one outer terminal of the potentiometer to **5V**.
2. Connect the other outer terminal to **GND**.
3. Connect the middle terminal (wiper) to **Analog Pin A0** on the Arduino.

**Wiring Summary:**
- Servo Signal: Pin 9
- Potentiometer Wiper: A0
- Shared Power Lines: Potentiometer (5V and GND), Servo (5V and GND)

**Illustration:**
![Potentiometer Wiring](https://i.imgur.com/jYNodVv.png)  
*Diagram showing potentiometer connected to 5V, GND, and A0.*

## Section Three: Writing the Code

### Step 1: Include Libraries

The Arduino IDE (and Wokwi) provides a Servo library for easy servo control. Include it at the top of your code:

```arduino
#include <Servo.h>
```

### Step 2: Define Pins and Create Servo Object

```arduino
Servo myServo; // Create a Servo object

int potPin = A0;   // Potentiometer connected to A0
int servoPin = 9;  // Servo connected to Pin 9

void setup() {
  myServo.attach(servoPin);  // Attach the servo to Pin 9
  Serial.begin(9600);        // For debugging if needed
}
```

### Step 3: Reading the Potentiometer and Controlling the Servo

In the `loop()` function:

- Read the analog value from the potentiometer (0 to 1023).
- Map this value to an angle between 0° and 180°.
- Set the servo position to the mapped angle.

```arduino
void loop() {
  int potValue = analogRead(potPin);           // Read the pot (0-1023)
  int angle = map(potValue, 0, 1023, 0, 180);  // Map to 0-180 degrees

  myServo.write(angle);  // Set servo to the calculated angle

  // Optional: Print the values for debugging
  Serial.print("Pot Value: ");
  Serial.print(potValue);
  Serial.print("  |  Servo Angle: ");
  Serial.println(angle);

  delay(15); // Small delay to smooth the servo movement
}
```

**Illustration:**
![Wokwi Code Editor](https://i.imgur.com/3RVHQ1u.png)  
*Example of where to paste code in the Wokwi code editor.*

## Section Four: Testing the Project

### Step 1: Start the Simulation

- Click on **"Start Simulation"** in Wokwi.

**Illustration:**
![Start Simulation Button](https://i.imgur.com/MZOdlpr.png)

### Step 2: Adjust the Potentiometer

- Click on the potentiometer in the simulation.
- A slider or knob should appear. Turn it and observe the servo arm rotating.
- As you change the potentiometer’s setting, the servo should smoothly rotate between 0° and 180°.

**Illustration:**
![Adjusting Potentiometer](https://i.imgur.com/ePrnZzv.png)

### Step 3: Troubleshooting

**Servo Not Moving?**
- Ensure servo signal wire is connected to Pin 9.
- Check if the servo is powered with 5V and GND.

**No Changes When Turning Potentiometer?**
- Verify the pot’s wiper is connected to A0.
- Ensure 5V and GND are connected to the outer pot terminals correctly.

## Section Five: Understanding the Logic

**Analog Input:**
The potentiometer sends an analog voltage (0 to 5V) to A0. The Arduino converts this into a digital value between 0 and 1023.

**Mapping to an Angle:**
Using the `map()` function, we convert the pot’s 0-1023 range into 0-180 degrees. This makes it intuitive to control the servo’s position.

**Servo Control:**
The Servo library takes care of generating the correct signals for the servo. You only need to specify the angle, and the servo will move accordingly.

## Section Six: Possible Enhancements

**Change Sensitivity:**
Add a smoothing function or a different mapping range to fine-tune servo movement.

**Add a Second Potentiometer:**
Control two servos (e.g., for a simple robotic arm joint).

**Include a Button:**
Use a button to toggle between automatic movement modes or to reset the servo position.

## Conclusion

You’ve now built a simple and educational project that shows how to:

- Read analog inputs from a potentiometer.
- Use the values to control a servo motor’s position.
- Understand the basics of input-to-output mapping in Arduino projects.

This foundational knowledge can be applied to more complex systems, such as robotic arms, pan/tilt camera mounts, or any interactive Arduino-based project involving precise motion control.

## Additional Resources

- **Wokwi Documentation**: [Wokwi Docs](https://docs.wokwi.com/)
- **Arduino Servo Library Reference**: [Servo Library Reference](https://www.arduino.cc/en/Reference/Servo)
- **Potentiometer Basics**: [All About Potentiometers](https://learn.sparkfun.com/tutorials/potentiometers)

By following these illustrated steps, you’ll have a clear, educational experience in building and understanding a simple servo control system. Enjoy exploring the world of Arduino!
