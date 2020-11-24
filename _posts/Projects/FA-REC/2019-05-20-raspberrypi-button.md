---
layout: post
title: "[Raspberry Pi] button"
categories: fa-rec
tag : [raspberry pi]
---
<div class="divider"></div>
/-- 필요한 것 --/

- Raspberry Pi 3 b+
- breadboard
- jumper wire
- button

<div class="divider"></div>

- **breadboard에 버튼 연결**<br>
![raspberry button 1](https://krispediadot.github.io/assets/images/raspberrypi_button_1.jpg)

- **GPIO 15번 핀을 사용** <br>
![raspberry gpio](https://krispediadot.github.io/assets/images/raspberrypi_gpio.jpg)

- **button에 연결한 wire를 15번 핀과 GND에 연결**<br>
![raspberry button 3](https://krispediadot.github.io/assets/images/raspberrypi_button_3.jpg)

- **테스트 코드**<br>

```python
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)
GPIO.setup(15, GPIO.IN, pull_up_down=GPIO.PUD_UP)

while True:
    input_state = GPIO.input(15)
    if input_state == False:
        print("Button was pushed!")
        time.sleep(0.2)
```