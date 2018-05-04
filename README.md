see the ttrash robot https://www.youtube.com/edit?o=U&video_id=JR9r6p7lBXw

	#include<servo.h>
        Servo servo;
	int const trigPin = 6;
	int const echoPin = 5;
	void setup()
	{
	pinMode(trigPin, OUTPUT); 
	pinMode(echoPin, INPUT); 
        servo.attach(3);
	}
	void loop()
	{       int duration, distance;
	digitalWrite(trigPin, HIGH); 
	delay(1);
	digitalWrite(trigPin, LOW);
	// Measure the pulse input in echo pin
	duration = pulseIn(echoPin, HIGH);
	// Distance is half the duration devided by 29.1 (from datasheet)
	distance = (duration/2) / 29.1;
	// if distance less than 0.5 meter and more than 0 (0 or less means over range) 
    if (distance <= 50 && distance >= 0) {
    	servo.write(50);
        delay(3000);
    } else {
    	
    	servo.write(160);
    }
    // Waiting 60 ms won't hurt any one
    delay(60);
	}﻿
