# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [Hello_LCD](#Hello_LCD)
* [FillMeInLAter](#FillMeInLAter)
---

## LED_Fade

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
void loop()
{

	for(int value = 0; value <=  255; value += 5) { //if value is equal 0 and less than or equal to 255 add +5 to value
		analogWrite(blink, value); // set of LED brightness to the value
		delay(30);
	for(int dash = 0; dash < value/10; dash++) { // when value goes up by 10 add "-"
		Serial.print("-"); 
	}
	Serial.println(value); // states brightness
	}
	for (int value = 255; value >= 0; value -=5) { //if value is equal 255 and more than or equal to 0 subtarct +5
		analogWrite(blink, value);
		delay(30);
		for(int dash = 0; dash < value/10; dash++) { // when value goes down by 10 subtract "-"
			Serial.print("-");
		}
		Serial.println(value); // states brightness

	}
```
The first *for* statemnet creates a function that will monitor the *value* and run the following code if the *value* holds true. In this function the *value* must be  equal to zero, or less than or equal to 255. If those conditions are true the *value* will gain 5, and then the *analogWrite* will turn on the LED and it will shine as bright as the *value* states. The second *for* statment creates a function that monitors the *dash* and run the following code in the *dash* holds true. In this function the *dash* must be equal to zero, or less than the *value* divided by ten. If those conditions are true the *dash* will increase and the serial monitor will print an amont of "-" relating to the *dash*.

### Evidence
https://create.arduino.cc/editor/helmstk1/9e044cca-43d7-4d93-885f-e6dec5b4f769/preview

### Images

<img src="https://github.com/lmcmind85/NotSoBasicArduino-1/blob/main/Images/LEDBlinkRevisited.jpeg?raw=true" width="500">

### Reflection

## Hello_LCD

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
link goes here

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

