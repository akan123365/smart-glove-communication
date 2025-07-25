# smart-glove-communication
A wearable embedded system that translates hand gestures into speech using Arduino, flex sensors, and Bluetooth to assist individuals with speech and hearing impairments

The project integrates flex sensors, an Arduino Uno, and Bluetooth communication to create a low-cost and portable assistive communication device.

## Table of Contents

- [Overview](#overview)
- [Objectives](#objectives)
- [Key Features](#key-features)
- [Hardware Components](#hardware-components)
- [System Architecture](#system-architecture)
- [Working Principle](#working-principle)
- [Circuit Diagram](#circuit-diagram)
- [Code](#code)
- [Results](#results)
- [Future Scope](#future-scope)
- [Demo Video](#demo-video)
- [Project Report](#project-report)
- [License](#license)

---

## Overview

The Smart Glove uses multiple flex sensors and a microcontroller to detect finger movements associated with specific hand gestures. These gestures are mapped to letters, words, or phrases. The data is processed and transmitted wirelessly to an Android device via Bluetooth, where the corresponding output is displayed or spoken.

---

## Objectives

- To develop an assistive communication device for the speech and hearing impaired.
- To translate predefined hand gestures into real-time audio/text.
- To ensure portability, low power consumption, and ease of use.

---

## Key Features

- Real-time gesture recognition
- Wireless communication using HC-05 Bluetooth module
- Compatible with Android smartphone for speech output
- Cost-effective and portable design
- Open-source and customizable gesture mapping

---

## Hardware Components

| Component              | Description                    |
|------------------------|--------------------------------|
| Arduino Uno            | Microcontroller board          |
| Flex Sensors (x5)      | Detect finger bending          |
| MPU6050 (optional)     | Motion tracking (optional)     |
| HC-05 Bluetooth Module | Wireless communication         |
| Battery Pack           | Power source                   |
| Jumper Wires, Gloves   | For interfacing and integration |

---

##  Working Principle

1. Flex sensors detect the bend in each finger and output analog signals.
2. Arduino reads these values and identifies gesture patterns.
3. Each gesture is mapped to a corresponding word/letter.
4. The gesture is transmitted via Bluetooth to a smartphone.
5. The Android app displays or speaks the recognized gesture.

---

## Circuit Diagram
![1000155854](https://github.com/user-attachments/assets/195bf852-65a6-48f9-834a-04a35c7947a8)



## Code
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2); // Set the LCD address

void setup() {
  Serial.begin(9600);
  lcd.init();           // Initialize the LCD
  lcd.backlight();      // Turn on the backlight
  lcd.setCursor(0, 0);
  lcd.print("SIGN LANGUAGE");
  pinMode(13, OUTPUT);  // Set pin 13 as output
}

void loop() {
  int s1 = analogRead(A0); // Sensor for "feeling cold"
  int s2 = analogRead(A1); // Sensor for "I am hungry"
  int s3 = analogRead(A2); // Sensor for "I need water"
  int s4 = analogRead(A3); // Sensor for "Emergency"

  Serial.println(s1); Serial.println("feeling cold");
  Serial.println(s2); Serial.println("I am hungry");
  Serial.println(s3); Serial.println("I need water");
  Serial.println(s4); Serial.println("Emergency");

  delay(3000); // Small delay before checking conditions

  if (s1 < 150) {
    digitalWrite(13, LOW);
    Serial.println("Feeling cold");
    lcd.setCursor(0, 1);
    lcd.print(" Feeling cold  ");
    delay(2000);
  }

  if (s2 < 200) {
    digitalWrite(13, HIGH);
    Serial.println("I am hungry");
    lcd.setCursor(0, 1);
    lcd.print(" I am hungry  ");
    delay(2000);
  }

  if (s3 < 150) {
    digitalWrite(13, LOW);
    Serial.println("I need water");
    lcd.setCursor(0, 1);
    lcd.print(" I need water ");
    delay(2000);
  }

  if (s4 < 130) {
    digitalWrite(13, HIGH);
    Serial.println("Emergency");
    lcd.setCursor(0, 1);
    lcd.print(" Emergency    ");
    delay(2000);
  }

  else {
    Serial.println("NOTHING");
    lcd.setCursor(0, 1);
    lcd.print(" NOTHING      ");
  }
} 
