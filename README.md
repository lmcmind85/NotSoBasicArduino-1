# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [Finite LED](#Finite_LED)
* [Arduino Reveiw](#Arduino_Reveiw)
* [Hello_LCD](#Hello_LCD)
* [FillMeInLAter](#FillMeInLAter)
---

## LED_Fade

### Description & Code

The goal is to make the LED fad in and out with *analogWrite* instead of *digitalWrite* and also have the Serial Monitor print "-" to symblozize wave to reseemble the brigtness of the LED.


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
		for(int dash = 0; dash < value/10; dash++) { // when value goes down by 10 add "-"
			Serial.print("-");
		}
		Serial.println(value); // states brightness

	}
```
The first *for* statement creates a function that will monitor the *value* and run the following code if the *value* holds true. In this function the *value* must be  equal to zero, and less than or equal to 255. If those conditions are true the *value* will gain 5, and then the *analogWrite* will turn on the LED and it will shine as bright as the *value* states. The second *for* statement creates a function that monitors the *dash* and run the following code in the *dash* holds true. In this function the *dash* must be equal to zero, and less than the *value* divided by ten. If those conditions are true the *dash* will increase and the serial monitor will print an amont of "-" relating to the *dash*. The next two *for* statemnets mirror the previous ones except the first *for* statement will decrease the value as long as the conditions of equal to 255, and more than or equal to 0.

### Evidence
[The Code in Arduino Editor](https://create.arduino.cc/editor/helmstk1/9e044cca-43d7-4d93-885f-e6dec5b4f769/preview)

### Images

<img src="https://github.com/lmcmind85/NotSoBasicArduino-1/blob/main/Images/LEDBlinkRevisited.jpeg?raw=true" width="500">

### Reflection

Using Examples in the Arduino Create is helpful to find new code and get help if your stuck.

## Finite_LED

### Description & Code

The goal is to make one LED blink 5 times, than another blink 5 times at a differnent pace.

```C++
int LED1 = 9; // first LED at pin 9
int LED2 = 8; // second LED at pin 8
int counter = 0;
int delayvar = 500; 

void setup() {
  Serial.begin(9600); 
  pinMode(LED1, OUTPUT); 
  pinMode(LED2, OUTPUT); 

}

void loop() {
  counter = counter + 1;      // adds one to the counter  
      Serial.println(counter); // prints the counter vaule.
      
  if (counter < 5) { // will run the following code as long as the counter < 5
    // This will make the LED blink once every 1/2 second
    digitalWrite(LED1, HIGH);   
    delay(delayvar);            
    Serial.println("Blink1");   
    digitalWrite(LED1, LOW);    
    delay(delayvar);            
  }
  
  else if (counter < 10) { // will run the following code as long as the counter < 10 AND if the counter isnt, it will reset the counter
        // This will make the LED blink once every 1/4 second
    digitalWrite(LED2, HIGH);  
    delay(delayvar/2); 
    Serial.println("Blink2");   
    digitalWrite(LED2, LOW);    
    delay(delayvar);            
  }
  else {
    counter = 0;
  }
}
```
We have two LED's at two different pins so these are stated at the begining of the code. We also have a variabe named *counter*. At the begining of our *void loop* the *counter* is increased by one. The following *else* statement will run the following code as long as the *counter* is less than 5. The following *else if* statement will run the following code as long as the *counter* is less than 10 and if not, it will reset the *counter*.

### Evidence
[The Code in Arduino Editor](https://create.arduino.cc/editor/helmstk1/9e044cca-43d7-4d93-885f-e6dec5b4f769/preview)

### Images

<img src="https://github.com/lmcmind85/NotSoBasicArduino-1/blob/main/Images/IMG_0737.JPG?raw=true" width="500">

### Reflection

Creating a new variable for a number you plan to use many or manipulate in diffent line of  code times is hlepful such as *delayVar* for my delays values. [This website](https://www.arduino.cc/reference/en/language/structure/control-structure/if/) provided by Mr. Hemlstetter helps explain how to create and use *if* statements.


## Arduino_Reveiw

### Description & Code

The goal is when I press the button  the LED will blink and then blink faster and faster. When I let go of the button, the blinking stops and resets the blink speed to 1 second.


```C++
int LED = 9;
int buttonState = 0;
int buttonPin = 2;
int delayVar = 1000;

void setup() {
  pinMode(LED, OUTPUT);
  pinMode(buttonPin, INPUT);
  Serial.begin(9600); // 
}

void loop() {
  buttonState = digitalRead(buttonPin);
  Serial.print("button State: ");
  Serial.print(buttonState);

  if (buttonState == HIGH) { // when button press run code
    blink(delayVar);
    Serial.print("\t delayVar:");
    Serial.println(delayVar);
    if (delayVar > 100)
      delayVar = delayVar - 100;
  }
  else
  {
    digitalWrite(LED, LOW); // when button not pressed run code           
    delayVar = 1000;
    Serial.println("\t no blink!");

  }
}

void blink(int x) { // function of blinking on a off
  digitalWrite(LED, HIGH);          
  delay(x);                       
  digitalWrite(LED, LOW);            
  delay(x);                       
}

```
The *if*/*else* statemnet in the loop will run the *blink* function and decrease the delay if the button is pressed. If not, it will remain off and reset delay.

### Evidence

[The Code in Arduino Editor](https://create.arduino.cc/editor/Lmcmind85/5202c69d-d734-4fe2-a233-c312240a619a/preview)

### Images

<img src="https://github.com/lmcmind85/NotSoBasicArduino-1/blob/219d268cfdbcaeb6ef21d440a4870a8c328bb712/Images/Screenshot%202020-12-09%20at%204.14.57%20PM.png?raw=true" width="500">

### Reflection

This assignment seemed to combine a lot of things from the prior assignments such as *if*/*else* statments and functions. I got stuck on this assignment due to my my *buttonPin* being set at 0. The pin 0 and 1 are used for serial communication.

## Hello_LCD

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
https://create.arduino.cc/editor/helmstk1/9e044cca-43d7-4d93-885f-e6dec5b4f769/preview

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

