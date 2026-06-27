# 1. Your Arduino IDE 

(1) Press the Check Mark button to verify your code. This compiles your code and tells you if you’ve written anything the computer can’t understand. Compiling means it converts the code you wrote to machine level code, instructions Maya can understand.         

(2) Press the Arrow button to compile then upload your code to the Maya’s brain. This means it sends the instructions via the USB cable to Maya’s brain.

(3) These are tabs, like the tabs in your internet browsers!

(4) This is where you put your code!

(5) This is the messages area. This area will tell you if you’ve made any mistakes in your code as well as other useful information.

(6) This opens the Serial Monitor, which is a window where the Maya can send you messages

```ino
#include ”Maya.h”

/*
Everything in this area is a “comment”. 
The computer ignores comments. 
*/

void setup() {
  // put your setup code here, to run once:

}

void loop() {
  // put your main code here, to run repeatedly:
}
```

- Don’t forget to include the Maya’s software library!
- Use comments to tell yourself or other human readers what the code is doing. In-line comments can be created by using a pair of forward slashes like this: //
- Each Maya  program has two required “functions”: setup(), and loop(). (Functions are also sometimes called routines or methods)
- setup(){} All the code between the two curly brackets {} will be run once when your Arduino program first runs.
- loop(){} This function is run after setup has finished. The code written between the two curly brackets {} will be run again, and again, until power is removed.
- You might be wondering what this void thing is, ignore this for now, it will be explained in a later chapter.

# 2 – Blink an LED

LEDs (light-emitting diodes) are small, powerful lights that are used in many different applications. Almost all modern flat screen televisions and monitors have LED indicator lights to show they are on or off.

To start off, we will work on blinking an LED. That’s right – it’s as simple as turning a light on and off. It might not seem like much, but establishing this important baseline will give you a solid foundation as we work towards more complex stuff!

```
#include “Maya.h”

LED led_object;

void setup(){
  delay(5000);
  led_object.enable(GREEN_PIN);
}

void loop(){
  led_object.turn_on();
  delay(1000);
  led_object.turn_off();
  delay(500); 
}
```

## What’s going on?

### `LED led_object;`

To be able to use an LED, we must first create (or instantiate) a LED object (here we named it led_object)  for each LED we want to use. LED is the class of the object led_object. led_object is an instance of the class LED. The name led_object is chosen arbitrarily, you can name it anything you like but it’s usually good practice to choose something according to its function or something you can easily remember.  You will learn more about objects and classes  later.

### `delay(5000);`

Maya’s brain is very very fast, capable of running thousands of lines of code each second. To slow it down so that we can see what it’s doing, we’ll often insert delays into the code. delay() is a function that counts in milliseconds (ms); there are 1000 ms in one second.

You can put numbers inside the parenthesis of delay(). To specify how long the delay will be in milliseconds, in this case you are passing the parameter or argument  5000 to the function delay().

You’ll learn more about functions/procedure and parameter/argument  later. Some people make a distinction about functions and procedures which we will discuss in a later chapter, but for our discussion we’ll use them interchangeably 🙂

### `led_object.enable(GREEN_PIN);`

For each object we create we must prepare it to be useable using the built-in method of  LED called enable() . We put GREEN_PIN, inside the parenthesis, which specifies that the  led_object we are referring to is the green one.

You might notice a similarity with delay(1000); and led_object.enable(GREEN_PIN); here, and you are correct. GREEN_PINis an argument/parameter, and you are passing it to the method enable(). But enable() has a special quality that is absent in the function delay(): it can only be used on objects with a class of LED such as led_object. This might be a little confusing, but don’t worry about it for now, it will make more sense later as we explore this concept more!

### `led_object.turn_on();`

We are instructing  led_object to turn on. You are right, turn_on() is a method of the LED class like enable()!

### `led_object.turn_off();`

We are instructing  led_object to turn off. You are right, turn_off() is a method of the LED class like enable() and turn_on() !

## Explore on Your Own

1. What happens when  instead of writing the  LED led_object; I forgot to write the semicolon? Each line of code must usually end in a semicolon. Look up the definition of syntax and syntax error  online, and write about what you’ve learned.
2. What should I do with the code if I wanted the LED turned on for two seconds and turned off for a quarter of a second? How bout if I wanted it turned on for 1/4 of a second and turned off for ¾ of a second?
3. What happens if instead of passing GREEN_PIN I pass YELLOW_PIN instead?
4. Using the original example code, what happens if instead of naming the object led_object, I named it green_led?  What do you think will happen if I pass YELLOW_PIN as an argument to green_led.enable()? Verify of your prediction is correct. Was your prediction correct? Why?

# 3 – Blink TWO LEDs

```

#include “Maya.h”

Led green_led, yellow_led;

void setup(){
  green_led.enable(GREEN_PIN);
  yellow_led.enable(YELLOW_PIN);

  yellow_led.off();
  green_led.off();
}

void loop(){
  green_led.on();
  delay(1000);
  green_led.off();
  delay(1000); 

  yellow_led.on();
  delay(1000);
  yellow_led.off();
  delay(1000); 
}
```

## Important!

You might be wondering more about this creation of the led_object and about the method led_object.turn_on() (why does it look slightly different from function delay()?).  . Look at the links below and summarize what you’ve learned in an article.

- http://study.com/academy/lesson/oop-object-oriented-programming-objects-classes-interfaces.html
- http://www.edibleapple.com/2011/10/29/steve-jobs-explains-object-oriented-programming/
- https://www.youtube.com/watch?v=MTfWr7o7Q4U

## Explore on your own

- (# 1) Before running the code above, what do you think does? Is your prediction correct? If it’s wrong, what did you miss?
- (# 2) Write code that will do the following sequence repeatedly forever:
  - Turn green LED on for half a second, then turn it off for half a second
  - Turn yellow LED on for half a second then turn it off for half a second
- (# 3) Do the same as #2  but instead of half a second only a quarter of a second.
- (# 4) Write code that will do the following sequence repeatedly forever:
  - For one second, both the yellow and green LED are on
  - For the next second, only the yellow LED is on
  - For the third second, only the green LED is on
  - For the fourth second, both LEDs are off
- (# 5) Do the same as #4 but instead on one second each, half a second each
- (# 6) Write code that turns the LEDs in an alternating fashion, each for a quarter of a second. That is, when the yellow LED is on the green LED is off and vice versa.
- (# 7) Do the same as #6 but instead of a quarter of a second, half a second long.
- (# 8) A blink is when an LED is on for a period of time and then off for a period of time. A blink of one second is such that is is on for one second and then off for one second. Write code that will do the following sequence repeatedly forever:
   - The green LED blinks for a ⅕ of a second five times
   - The yellow LED blinks for half a second three times 
