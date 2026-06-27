# Moving Maya
Maya has two continuous servo motor with wheels. You can make her turn left, right, go forward and backward like in the code below.

```
#include "Maya.h" 

Motors motors;

void setup(){
  motors.enable();
}

void loop(){

  motors.move_backward();
  delay(2000);
  
  motors.move_forward();
  delay(2000);

  motors.turn_left();
  delay(3000);

  motors.turn_right();
  delay(3000);
}
```

## Coding Exercises
Can you make Maya follow one of the paths below? How many can you do in one hour?

🎇 Picture of Paths

Can you make Maya do cool things like the ones shown in this video?

📺 Video of Maya's Movement

Learn More about Motors
To learn more about Maya’s motors at a deeper level you can check out the following pages:

- How to make Maya follow a “straighter path”
- How to make Maya draw  small and large circles 
- What is a continuous servo? How does it work?
- Technical specifications of Maya’s specific motors: what do these words and numbers even mean?
- Code Discussion: Maya’s Motor Class


# Making Music

Maya has a Piezo element  you can use to play sounds. Maya’s brain can send a signal that causes the Piezo element to bend and flex. This moves the air around and creates the sound we can hear. The closer the waves, the higher the note. The measure of how close the waves is called the frequency (Hz).

🎇 Picture of Piezo

The note Middle C is defined as the frequency of 261 Hz. If Maya’s Brain sends a high and low signal evenly 261 times a second to the Piezo, we will hear the Middle C. Maya’s library does this for you and has even predefined the notes which you can use.

```
#include "Maya.h"

Piezo piezo;

#define c 261
#define d 294
#define e 329
#define f 349
#define g 392

const int length = 10;
int frequency[10] = {c, d, e, f, g, g, f, e, d, g};
int duration = 300;

void setup() {
  piezo.enable();
}

void loop() {
  for (int i = 0; i < length; i++)
    piezo.play_tone(frequency[i], duration);
}
```
You can also make Maya do a sweeping sound or like an “alarm type of sound” like the ones we can hear in a burglar alarm.

- Coding Exercises
- Can you explain what is happening in the code above?
- Can you make Maya play the tune of your favorite song?
- From the previous exercise of Maya drawing crazy patterns, can you make Maya beep three times every time she changes direction? (play the note F before turning left, the note A before turning right, and the note G before going forward)
- Building from the challenge above, can you make Maya play a victory song every when she finally completes the path you specified?

## Learn More About The Piezo
- Sample codes:  50+ different melodies 
- Sample code: (sine wave) burglar alarm sound
- Sample code: sweeping sound
- Piezo: predefines notes, documentation, sample usage
- Code Discussion: Piezo Class
- Piezo: Technical Specifications

 
# Mixing Colors

Maya has four “pixels”. Each pixel has red, green, and blue colors and you can specify the quantity of each color. 

🎇 Picture of Neopixels

By controlling the quantity of each you can mix pretty much any color you want.

🎇 Picture of Color Wheels and Color Truth Table 

Your eye has three types of light receptor in it (red, green and blue). Your eye and brain process the amounts of red, green ,and blue and convert it into a color of the spectrum. In a way, we are playing a trick on the eye. This same idea is used in TV displays and computer screens – the  red, green and blue color dots next to each other making up each pixel.

🎇 More pictures of color wheels

```
#include "Maya.h" 

Pixels pixels;

void setup(){
  pixels.enable();
}

void loop(){

  pixels.left_most(75, 75, 0);    
  pixels.left_center(0, 75, 75)   
  pixels.right_center(75, 0, 75); 
  pixels.right_most(75, 75, 75);
  delay(1000);
  
  pixels.off();
  delay(1000);
}
```

What matters when mixing colors is the ratio of the colors you mix. Check out this code. All the pixels show the same color orange but with different intensities for the first part. On the second part, the Maya shows different shades of purple increasing their likeness to blue as you go down the code (the ratio of blue to red increases).

We have also predefined some functions and colors for you to use to make your life easier. Check this code. Pretty cool huh? 

```
#include "Maya.h" 

Pixels pixels;

void setup(){
  pixels.enable();
}

void loop(){

  // displaying different predefined colors
  pixels.display(LEFT_MOST_PIX, PINK);
  pixels.display(LEFT_CENTER_PIX, AQUA);
  pixels.display(RIGHT_CENTER_PIX, PURPLE);
  pixels.display(RIGHT_MOST_PIX, LIME);
  delay(1000);
  
  pixels.off()
  delay(1000);
  
  //display different prefined colors - shortcut
  pixels.show_all(RED, GREEN, BLUE, INDIGO)
  delay(1000);
```

## Code Exercise
- What does the sample code above do? Can you explain why? Can you changed the parameters passed on the code to display your favorite colors? And after the path is finished, while playing a victory song, can you make her display colorful patterns of light that matches the beat of the song?
- Can you code the following sequence below (half a second each state), display each of the 12 predefined colors in the Maya’s Library? 🎇 Picture of the sequence
- Building up on the previous exercise, every time Maya changes direction she beeps three times. Can you display a different random color every time she beeps?
- Using a for-loop, can you make all of Maya’s pixels display a sequence of increasing and decreasing intensity of orange? How about white?
- Using a for-loop, can you make all of Maya’s pixels display a sequence for purple varying from most “red-ish” to “blue-ish” and then “blue-ish” to “red-ish” ?
- What other cool patterns can you make using Maya’s four pixels?

🎇 Check out some cool patterns you can make with Maya’s four pixels

## Learn More About Pixels
- Code Discussion: Pixel Class
-  Documentation and Technical Specification of Maya’s Pixels
-  Did you know that all of these Pixels are controlled using only one signal? Cool huh?
- More sample code of pixel patterns

🎇 Picture of Pixels

# Measuring Distance

🎇 Picture of Ultrasonic Sensor

Maya has a sensor that measures distance with sound waves. It finds objects like a bat or dolphin does. One part of the sensor is a speaker that sends out a sound wave and the other part is a microphone that measures how long it takes for the object to come back. The longer it takes to come back, the further away the object.

🎇 Picture of how ultrasonic waves travel 

The speaker sends the object out in a cone, so only the objects within the cone will return sound and be detected. This sensor cannot detect individual objects only how long it took the sound sent to return. It measures the closest object.

🎇 Picture of ultrasonic waves with various objects

If an object absorbs sound, or if there is nothing for a long distance or if the object bounces the sound at an angle. There might not be enough sound returning to measure anything.

🎇 Picture of what it will fail to detect

```
#include "Maya.h"

Ping ping; 

void setup() {
  ping.enable();
  Serial.begin(9600);
}

void loop() {

  Serial.print(" cm: ");
  Serial.print(ping.centimeters());
  
  Serial.print(" inches: ");
  Serial.println(ping.inches());
  delay(500);
}
```
🎇 Picture of what it will fail to detect

## Coding Exercise

- Put a notebook in front of the sensor at varying distances. Measure the distances between Maya and your hand with a ruler/measuring tape. Do the readings make sense?
- Try putting a notebook far or at an angle, what angle and distance does the distance sensor fail? Can the sensor detect your pillow? How about a sponge
- Theremin Maya – The farther the obstacle Maya detects the higher frequency Maya produces, the nearer the obstacle Maya detects the lower the frequency. If the obstacle is too far away, Maya stays silent. Also display different colors of the pixels depending on the intensity.
- Make Maya display a “progress bar” with its four pixels depending on how far away the obstacle is from Maya. Instead of a progress bar, make the intensity vary with distance.
- Station Keeping – Maya always wants to be five inches away from your hand, if your hand is too near she will move backward until she is five inches away from your hand. If your had is too far, she will move forward until she is five inches away from hand. If she can’t detect your hand, she will stay where she is. 
- Stop rotating when Detected. Maya continuous rotating until you put an obstacle two to three inches away from her face
- Obstacle Avoidance – Maya wanders autonomously, if it detects an obstacle that is too near  it turns until it’s fine for her to wander autonomously again. 
- Sensing Turtle Maya I (Motor, Neopixels, Piezo)

## Learn More About Distance Sensors
- Code Discussion: Ping Class
- More cool stuff about Maya’s distance sensor
- Sample codes with Maya’s distance sensor

# Sensing Light and Darkness

Maya has two sensors that detect the level of light that hits them. These sensors are phototransistors – when more light hits them, the higher the signal they send to Maya’s brain.

🎇 Picture of Maya's Light Sensors

Maya sees the amount of light in terms of an integer. The more light, the higher the number. Each sensor is slightly different, so the same amount might not mean the same number for each sensor.

```
#include "Maya.h"

AnalogReadings line_sensor; 

void setup() {
  light_sensor.enable(PIN_LIGHT_LEFT, PIN_LIGHT_RIGHT);
  Serial.begin(9600);
}

void loop() {

  Serial.print(" | light left: ");
  Serial.print(light_sensor.left());
  Serial.print(" | light right: ");
  Serial.println(light_sensor.right());

  delay(1000);
}
```

The closer the sensor is to the light, the stronger the light from the light source. The light arriving at the the sensor nearest to the light source is going to be the strongest, and the sensor farthest to the light source is going to receive the least amount of light. Just like being further away from someone yelling makes it quieter, being further away makes the light dimmer.

🎇 Visualization of Light Waves

## Code Exercise
- Light following. Write code such that Maya will follow a flashlight. (Hint: if Maya’s left sensor reading is higher than Maya’s right sensor reading what should Maya do?)
- Light avoidance. Write code such that Maya will avoid a flashlight.
- Rotate until light detected. Write code such Maya will rotate in place until it sees the light of the flashlight. One the light of the flashlight is gone, it will proceed to rotating again
- Cool intruder detector and automatic night light! When the lights of the room is off at night, Maya will display light from its Pixels. When you turn on the light, Maya will make alarming sounds with its Piezo and rotate in place.
- Sensing Turtle Maya II. Building up from the earlier exercises, Maya will detect that she has reached the end of the path which is inside a dark box. Only when she detects the darkness will she play the victory song.

## Learn more about Light Sensors
- Code Discussion: AnalogSensor Class
- More sample code with Maya using her light sensors
- Technical specifications: Photo Transistor


# Projects with Maya

# Expanding Maya

Maya has expansion pins which you can hook-up a lot of cool modules. Here are some examples of things you can hook-up to Maya ( from various popular distributors like DFRobot, Sparkfun and Adafruit), how to use them and sample projects.

- Sound sensor (analog)
- PIR (analog)
- IR + Remote (analog)
- RTC (i2c)
- Gesture sensor (i2c)
- 8 x 16 Led Matrix (i2c)
- Bluetooth (tx/rx)
- Color sensor (i2c)
- Joystick (2 analog + digital)
- Potentiometers (2 analog)
- MPU6050 (i2c)

## Sound sensor (analog)

- If Maya is moving and she hears a loud sound, she will stop. If Maya is stationary and she hears a loud sound she will start moving.
- If Maya hears a moderately loud sound she will make a sweeping sound and display a pattern with her pixels. If she hears a really loud sound she will start rotating for three seconds.
- Have Maya’s lights respond to the beat of the music playing.

## PIR (digital)

Everytime Maya senses a movement, she will make an alarming sound, display a pattern with her pixels and rotate for three seconds.

## IR + Remote (digital)

Control Maya using an IR remote

## RTC (i2c)

Every 15 minutes,  Maya will rotate in place and beep. You can also ask Maya what time it is by covering her eyes.

## Gesture Sensor (i2c)

Depending on your  gesture (up, down, left, right), Maya will go forward, backward, left, right for two seconds

## 8 x 16 led matrix ( i2c )

Maya rotates and each time you cover her eyes she will stop and  display a random short animation in her 8x 16 led matrix.

## Bluetooth (Rx, Tx)

Control Maya remotely via phone or computer

## Color sensor (i2c)

Maya will display the color you made her sense with a color sensor. Maya will also perform the action assigned to the color you specified.

## Joystick (2 analog + digital)

Maya will Move via Joystick Control

## Potentiometer (2 analog)

- Maya will make a sound on how you much turn the two potentiometers
- The amount or red and blue that Maya displays will depend on the values of the two potentiometers

## MPU6050 IMU Sensor (i2c)

Maya will move depending on the orientation of the IMU sensor
