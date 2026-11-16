

```
from machine import Pin
onboardLED = Pin(25, Pin.OUT)
onboardLED.value(1)

```


```
Pin.PULL_DOWN
```
- We use 3.3V to signal HIGH and trigger certain pieces of code.
- PULL_DOWN means that instead of floating between 3.3v-0v, its always low to start with
- Could achieve this with resistors, but pico has this functionality built in

```
.toggle()
```
- Toggle LED state with no additional logic