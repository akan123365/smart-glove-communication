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

## System Architecture
---

##  Working Principle

1. Flex sensors detect the bend in each finger and output analog signals.
2. Arduino reads these values and identifies gesture patterns.
3. Each gesture is mapped to a corresponding word/letter.
4. The gesture is transmitted via Bluetooth to a smartphone.
5. The Android app displays or speaks the recognized gesture.

---

## Circuit Diagram


## Code
