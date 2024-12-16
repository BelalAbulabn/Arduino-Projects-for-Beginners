
# Arduino Traffic Light Simulation

## Introduction

In this tutorial, you’ll learn how to create a simple traffic light simulation using an Arduino and three LEDs (Red, Yellow, and Green). This project introduces basic digital output control, timing, and sequencing. By the end, you will understand:

- How to connect and control multiple LEDs.
- How to use `digitalWrite()` and `delay()` to create timed sequences.
- A simple way to mimic a traffic light cycle.

## Prerequisites

- **Internet Access**: We’ll use the [Wokwi Arduino Simulator](https://wokwi.com/).
- **Modern Web Browser**: Chrome, Firefox, or similar.
- **Basic Arduino Knowledge**: Helpful but not required.

## Section One: Setting Up the Wokwi Environment

### Step 1: Create a New Project

1. Go to [Wokwi Arduino Simulator](https://wokwi.com/).
2. Click on **"Start Creating"** or go directly to [New Arduino Uno Project](https://wokwi.com/projects/new/arduino-uno).

**Illustration:**
![Wokwi New Project](https://i.imgur.com/lJZFm53.png)

### Step 2: Adding Components

- **Arduino Uno**: Provided by default.
- **LEDs (3x)**: Red, Yellow, Green LEDs.
- **Resistors (3x)**: 220Ω each.
- **Wires** for connections.

**Illustration:**
![Adding LEDs](https://i.imgur.com/VaaFgSN.png)

## Section Two: Wiring the Components

We’ll connect each LED to a different Arduino digital pin through a resistor. The recommended setup is:

- Red LED → Pin 8
- Yellow LED → Pin 7
- Green LED → Pin 6

### Step 1: Red LED Wiring

1. Place the **Red LED** on the breadboard.
2. Connect the **LED Anode (+)** through a **220Ω resistor** to **Pin 8**.
3. Connect the **LED Cathode (-)** to the Arduino **GND**.

**Illustration:**
![Red LED Wiring](https://i.imgur.com/KQcd9aH.png)

### Step 2: Yellow and Green LED Wiring

Repeat the same steps for the other LEDs:

**Yellow LED**:
- LED Anode (+) through a 220Ω resistor to **Pin 7**.
- LED Cathode (-) to **GND**.

**Green LED**:
- LED Anode (+) through a 220Ω resistor to **Pin 6**.
- LED Cathode (-) to **GND**.

**Wiring Summary:**
- Red LED → Pin 8
- Yellow LED → Pin 7
- Green LED → Pin 6
- All LED cathodes to GND (can share a single GND line)

**Illustration:**
![All LEDs Wired](https://i.imgur.com/jYNodVv.png)

## Section Three: Writing the Code

### Step 1: Define the LED Pins

Open the **"Code"** tab in Wokwi and enter:

```arduino
int redLED = 8;
int yellowLED = 7;
int greenLED = 6;

void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}
```

### Step 2: Creating the Traffic Light Sequence

In the `loop()` function, we’ll create a sequence:

1. **Green Light ON**:  
   Green ON for 3 seconds, others OFF.
2. **Yellow Light ON**:  
   Yellow ON for 1 second, others OFF.
3. **Red Light ON**:  
   Red ON for 3 seconds, others OFF.

```arduino
void loop() {
  // Green phase
  digitalWrite(greenLED, HIGH);
  digitalWrite(yellowLED, LOW);
  digitalWrite(redLED, LOW);
  delay(3000); // Green on for 3 seconds

  // Yellow phase
  digitalWrite(greenLED, LOW);
  digitalWrite(yellowLED, HIGH);
  digitalWrite(redLED, LOW);
  delay(1000); // Yellow on for 1 second

  // Red phase
  digitalWrite(greenLED, LOW);
  digitalWrite(yellowLED, LOW);
  digitalWrite(redLED, HIGH);
  delay(3000); // Red on for 3 seconds
}
```

**Illustration:**
![Wokwi Code Editor](https://i.imgur.com/3RVHQ1u.png)

## Section Four: Testing the Project

### Step 1: Start the Simulation

- Click on **"Start Simulation"** in Wokwi.

**Illustration:**
![Start Simulation Button](https://i.imgur.com/MZOdlpr.png)

### Step 2: Observe the LED Sequence

- After starting the simulation, watch the LEDs cycle:
  - Green LED lights for 3 seconds.
  - Yellow LED lights for 1 second.
  - Red LED lights for 3 seconds.
- This cycle repeats indefinitely, just like a traffic light.

**Illustration:**
![Traffic Light Simulation](https://i.imgur.com/ePrnZzv.png)

### Step 3: Troubleshooting

**No LED Lighting Up?**
- Check the pin connections for each LED.
- Ensure the LED is not reversed (long leg is anode).
- Verify resistors are placed correctly.

**Sequence Too Fast or Too Slow?**
- Adjust the `delay()` values in the code to change timings.

## Section Five: Understanding the Logic

- **Digital Outputs**: We used `pinMode(…, OUTPUT)` to set the pins controlling LEDs.
- **LED Control**: `digitalWrite(pin, HIGH)` turns the LED ON; `digitalWrite(pin, LOW)` turns it OFF.
- **Timing**: `delay()` pauses the program, creating a timed sequence for the traffic lights.

## Section Six: Possible Enhancements

- **Add a Pedestrian Crossing**: Use a button to change the sequence or turn on a pedestrian LED.
- **Use PWM for Brightness Control**: On PWM pins, vary brightness by changing `analogWrite()` values.
- **Advanced Sequencing**: Use `millis()` for non-blocking timing, allowing more complex interactions.

## Conclusion

You’ve created a basic traffic light simulation that:
- Demonstrates digital output control.
- Uses simple timing to create a repeating LED sequence.

This foundational understanding can be applied to more complex projects, such as real-time control systems, interactive installations, or learning how to handle multiple outputs simultaneously.

## Additional Resources

- **Wokwi Documentation**: [Wokwi Docs](https://docs.wokwi.com/)
- **Arduino Reference**: [Arduino Language Reference](https://www.arduino.cc/reference/en/)
- **LED Basics**: [LED Guide](https://learn.sparkfun.com/tutorials/light-emitting-diodes-leds)

By following these illustrated steps, you’ve gained experience in controlling multiple LEDs and creating timed sequences. Enjoy exploring more Arduino possibilities!
