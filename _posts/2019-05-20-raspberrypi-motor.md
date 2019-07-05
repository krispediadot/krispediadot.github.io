---
layout: post
title: "[Raspberry Pi] DC Motor"
categories: farec
tag : [raspberry pi]
---
<div class="divider"></div>
/-- 필요한 것 --/

- Raspberry Pi 3 b+
- jumper wire
- DC Motor
- power
- L298N dual motor controller modules

<div class="divider"></div>

- **GPIO 18/23/24/7/8/12 번 핀 사용**<br>
![raspberry gpio](https://krispedia.github.io/assets/images/raspberrypi_gpio.jpg)

- **Motor controller 사용**<br>

파란 박스 부분에 wire 연결<br>
![raspberry motor controller](https://krispedia.github.io/assets/images/raspberrypi_motor_shield.jpg)

- **Motor controller 1번 부분에 GPIO 핀 연결**<br>
    
    | Motor controller | GPIO |
    | ---------------- | :---:|
    | enA              | 18   |
    | pin1             | 23   |
    | pin2             | 24   |
    | pin3             | 7    |
    | pin4             | 8    |
    | enB              | 12   |

![raspberry motor 1](https://krispedia.github.io/assets/images/raspberrypi_motor_1.jpg)

- **Motor controller 2번 부분에 power 연결**<br>

    | Wire             | Motor controller |
    | ------------     | :---------------:|
    | DC Motor wire    | motorA & motorB  |
    | power red wire   | 5V               |
    | power black wire | GND              |

![raspberry motor 2](https://krispedia.github.io/assets/images/raspberrypi_motor_2.jpg)

- **테스트 코드**<br>

```python
import RPi.GPIO as GPIO
import sys
import time

GPIO.setmode(GPIO.BCM)
enA = 18
pin1 = 23
pin2 = 24
pin3 = 7
pin4 = 8
enB = 12

GPIO.setup(enA, GPIO.OUT)
GPIO.setup(pin1, GPIO.OUT)
GPIO.setup(pin2, GPIO.OUT)
GPIO.setup(enB, GPIO.OUT)
GPIO.setup(pin3, GPIO.OUT)
GPIO.setup(pin4, GPIO.OUT)

MODE = 0

try:
    MODE = int(input("Plz enter number: "))
    if MODE == 0:
        while True:
            print('Motor1')
            GPIO.output(pin1, True)
            GPIO.output(pin2, False)
            GPIO.output(enA, False)
            GPIO.output(pin3, True)
            GPIO.output(pin4, False)
            GPIO.output(enB, False)
            time.sleep(2)
            
            
    elif MODE == 1:
        while True:
            print('Motor1')
            GPIO.output(pin1, True)
            GPIO.output(pin2, False)
            GPIO.output(enA, True)
            GPIO.output(pin3, True)
            GPIO.output(pin4, False)
            GPIO.output(enB, True)
            time.sleep(2)
            
        
except KeyboardInterrupt:
    GPIO.cleanup()
    sys.exit()

```  

- **[button](https://krispedia.github.io/raspberrypi-button)과 함께 연결한 모습**<br>

![raspberry motor 3](https://krispedia.github.io/assets/images/raspberrypi_motor_3.jpg)