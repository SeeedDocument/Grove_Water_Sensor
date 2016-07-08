# Grove - Water Sensor
***
### Introduction
***
The Water Sensor module is part of the Grove system. It indicates whether the sensor is dry, damp or completely immersed in water by measuring conductivity. The sensor traces have a weak pull-up resistor of 1 MΩ. The resistor will pull the sensor trace value high until a drop of water shorts the sensor trace to the grounded trace. Believe it or not this circuit will work with the digital I/O pins of your Arduino or you can use it with the analog pins to detect the amount of water induced contact between the grounded and sensor traces.

Model:[SEN113104](https://www.seeedstudio.com/item_detail.html?p_id=748)

![](https://raw.githubusercontent.com/SeeedDocument/Grove_Water_Sensor/master/image/Grove_Water_Sensor%20pic1.jpg)

### Features
***
- Grove compatible interface
- Low power consumption
- 2.0cm x 2.0cm Grove module
- High sensitivity
### Applications Ideas
***
- Rainfall detecting
- Liquid leakage
- Tank overflow detector
### Cautions
***
This device is for educational and hobby applications only. It is not intended to be used in applications where its malfunction could result in damage to property or human safety.
### Specification
***

|Item|	Min|	Typical|	Max|	Unit|
|:------|:------------------|:------------------|:------------------|:------------------|
|Working Voltage|	4.75|	5.0	|5.25|	V|
|Current|||	<20|	mA|
|Working Temperature|	10	|-|	30|	℃|
|Working Humidity (without condensation)|	10|	-|	90|	 %|

### usage
***
**With  Arduino**

Connect the module to the Basic board using any of the digital pin. You can gain the value of the signal pin. When there is water on the bare conducting wires, the value is LOW. Otherwise, it will be HIGH.The following sketch demonstrates a simple application of using the Water sensor to control the buzzer. As the picture on the below indicates, the Water sensor is connected to digital port 8 of the [ Grove - Basic Shield](http://www.seeedstudio.com/wiki/Grove_-_Base_Shield)and the Buzzer is connected to digital port 12. When there is water on the bare conducting wires, the SIG pin output a LOW voltage. Then the Buzzer sounds. The hardware installation is as follows:

![](https://raw.githubusercontent.com/SeeedDocument/Grove_Water_Sensor/master/image/Grove_Water_Sensor%20pic2.jpg)
- Then connect Arduino to PC by using a USB cable.
- Copy and paste code below to a new Arduino sketch.
```Javascript
 /*macro definition of water sensor and the buzzer*/
#define WATER_SENSOR 8
#define BUZZER 12
void setup()
{
	pins_init();
}
void loop()
{
	if(isExposedToWater())
		soundAlarm();
}
void pins_init()
{
	pinMode(WATER_SENSOR, INPUT);
	pinMode(BUZZER, OUTPUT);
}
/************************************************************************/
/*Function: When the sensor is exposed to the water, the buzzer sounds	*/
/*			for 2 seconds.												*/
void soundAlarm()
{
	for(uint8_t i = 0;i < 20;i ++)
	{
		digitalWrite(BUZZER, HIGH);
		delay(50);
		digitalWrite(BUZZER, LOW);
		delay(50);
	}
}
/************************************************************************/
/*Function: Determine whether the sensor is exposed to the water		*/
/*Parameter:-void           											*/
/*Return:	-boolean,if it is exposed to the water,it will return true. */
boolean isExposedToWater()
{
	if(digitalRead(WATER_SENSOR) == LOW)
		return true;
	else return false;
}
```
- Upload the code, Please click [ here](http://www.seeedstudio.com/wiki/Upload_Code) if you do not know how to upload.
- The buzzer sounds when the sensor is damp or completely immersed in water. Have a try!

### With [  Raspberry Pi](http://www.seeedstudio.com/wiki/GrovePi%2B)

1.You should have got a raspberry pi and a grovepi or grovepi+.

2.You should have completed configuring the development enviroment, otherwise follow [ here](http://www.seeedstudio.com/wiki/GrovePi%2B#Introducing_the_GrovePi.2B). 

3.Connection 
- Plug the sensor to grovepi socket D2 by using a grove cable.

4.Navigate to the demos' directory: 
```Javascript
 cd yourpath/GrovePi/Software/Python/
```
- To see the code
```Javascript
  nano grove_water_sensor.py   # "Ctrl+x" to exit #
```
```Javascript
import time
import grovepi

# Connect the Grove Water Sensor to digital port D2
# SIG,NC,VCC,GND
water_sensor = 2

grovepi.pinMode(water_sensor,"INPUT")

while True:
    try:
        print grovepi.digitalRead(water_sensor)
        time.sleep(.5)

    except IOError:
        print "Error"
```
5.Run the demo.
```Javascript
  sudo python grove_water_sensor.py
```
### Resources
***
- [ Water Sensor Eagle Files](https://github.com/SeeedDocument/Grove_Water_Sensor/tree/master/resource)
- [ Demo code for Water Sensor (new)](https://github.com/Seeed-Studio/Grove_Water_Sensor)

### Support
***
If you have questions or other better design ideas, you can go to our [forum ](http://www.seeed.cc/)or [wish ](http://www.seeedstudio.com/wiki/index.php?title=Main_Page&uselang=en) to discuss.

