In the next few paragraphs, we will discuss energy, power, and energy/power sources. You will encounter these concepts over and over again as we try to understand how Maya’s various electronics components work in greater detail.

In order for Maya to do things, she needs a source of energy or power, much like how human beings need to eat food in order stay alive or do things. In simple terms, Maya needs energy in order to do work, Maya uses energy to do work. Energy is not an infinite resource. Each time Maya works, the energy from her battery gets depleted. Power is just how much energy Maya uses per second (or any unit of time).

🎇 Battery drawing 

Maya’s source of energy or power is her batteries. Without an energy/power source like batteries, electrons will not be able to flow in the circuit. Electrons in Maya is like blood flowing in a human beings body. If electrons aren’t flowing, Maya is dead.

Electrical power can be measured in Watts which just the product of current and voltage. P = I*V. Energy is measured in watt-hours or how much power you can give in an hour. Although not as accurate, when it comes to Maya’s energy source like batteries, energy can be roughly measured in (Ah) or how much current you can get from the battery in an hour. Check Sparkfun’s power tutorial to see this equation at work.


🎇 Circuit Diagram

A battery contains a carefully controlled chemical reaction that puts the electrons in from the positive terminal and pushes them out of the negative terminal. The strength of which the electrons are pushed are measured in volts (V) which is also known as an electric potential difference. Measured in amps (A) is the electric current which is how many electrons a battery can push per second. A current of 1 A is about 6×10^(18) electrons flowing out of one side and into the other.

🎇 Battery Voltage vs. Current

If you attempt to draw more and more current, the voltage produced by the battery will drop eventually dropping to zero which is equivalent to a short circuit current, the current that flows if you connect one side directly to another with a wire. If you try this, the battery could explode. SO DON’T DO IT!

🎇 Visualization of Electron Flow 

The power (W- watts) put out of the battery can be measured by the product of current with the voltage. If you want more power, you need to add more batteries. If you connect batteries in parallel, the voltage stays the same but the maximum current output will be multiplied by the number of batteries. If you connect them in series, the maximum current stays the same but the voltage multiplies. In practice, we only connect batteries in series because in real life, batteries will have slightly different voltages so if they are connected in parallel, the stronger battery will deliver current to the weaker battery wasting power.

🎇 More pictures of batteries

A rough measure of the amount of energy stored in a battery is given by its milli-amp-hour (mAH) rating. This specifies how long the battery will last at the given discharge rate. If you draw current at a rate of 200 mA, and the battery lasts for 3 hours, this is a 600 mAH battery. If you discharge the same battery at 600 mAh you would get roughly an hour of operation. Of course, in practice, the battery capacity tends to decline with higher discharge rates so you might get only 50 minutes. Once the chemicals of a battery are exhausted, the battery will stop producing power which happens gradually like shown in the graph below.

🎇 Chart of battery voltage over time 

So if you see that Maya’s not working like she used to, it might mean that her battery is running low and you might want to replace her batteries with a new set of fresh batteries.

##References

- Adafruit’s all about batteries
- Sparkfun’s electrical power
- Pololu 3Pi’s Robot Guide
