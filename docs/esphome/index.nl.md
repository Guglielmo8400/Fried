# ESPHome documentatie

Deze pagina bevat de refentie code voor elke onderdeel op de badge. We gaan er van uit dat je [esphome](https://esphome.io/guides/getting_started_command_line) reeds geïnstalleerd hebt en vertrouwd bent met het toevoegen van een toestel.

## Gemeenschappelijke code

```
substitutions:
  esphome_name: fri3d2024

esphome:
  name: ${esphome_name}

esp32:
  board: esp32-s3-devkitc-1
  framework:
    type: arduino
```

## Scherm

```
spi:
  clk_pin: GPIO7
  mosi_pin: GPIO6

display:
  - platform: ili9xxx
    model: ST7789V
    dimensions:
      height: 240
      width: 296
    transform:
      swap_xy: true
      mirror_x: false
    data_rate: 80MHz
    dc_pin: GPIO4
    cs_pin: GPIO5
    reset_pin: GPIO48
    auto_clear_enabled: false
    lambda: |-
      it.image(0, 0, id(my_image));
#      it.print(0, 0, id(my_font), "Hello World!");
#      it.printf(0, 15, id(my_font), TextAlign::BASELINE_LEFT, "%.1f graden", id(temperature).state);
# sensor.living_room_temperature
#      it.line(0, 0, 50, 50);

font:
  - file: "opensans.ttf"
    id: my_font
    size: 20

image:
  - file: "fri3d.png"
    id: my_image
    type: RGB24
```

_TODO_

- refresh log error

## Status LED

```
light:
  - platform: status_led
    name: "State"
    id: "state"
    pin: GPIO21
```

## RGB LEDs

```
light:
  - platform: neopixelbus
    type: GRB
    variant: WS2812
    pin: GPIO12
    num_leds: 5
    name: "NeoPixel Light"
```

## Drukknoppen

```
binary_sensor:
  - platform: gpio
    pin:
      number: GPIO39
      mode:
        input: true
        pullup: true
      inverted: true
    name: "A"
  - platform: gpio
    pin:
      number: GPIO40
      mode:
        input: true
        pullup: true
      inverted: true
    name: "B"
  - platform: gpio
    pin:
      number: GPIO38
      mode:
        input: true
        pullup: true
      inverted: true
    name: "X"
  - platform: gpio
    pin:
      number: GPIO41
      mode:
        input: true
        pullup: true
      inverted: true
    name: "Y"
  - platform: gpio
    pin:
      number: GPIO45
      mode:
        input: true
        pullup: true
      inverted: true
    name: "menu"
  - platform: gpio
    pin:
      number: GPIO0
      mode:
        input: true
        #pullup: true
      inverted: true
    name: "start"
```

## Joystick

```
sensor:
  - platform: adc
    id: joystick_x
    name: "Joystick X axis"
    pin: GPIO01
    internal: True
    attenuation: auto
    update_interval: 500ms

  - platform: adc
    id: joystick_y
    name: "Joystick Y axis"
    pin: GPIO03
    internal: True
    attenuation: 11db
    update_interval: 500ms
```

_TODO_

- disable logging
- on_xxx: left/right & up/down

## Zoemer

```

```

_TODO_

- test

## Accelerometer

```
i2c:
  sda: GPIO9
  scl: GPIO18
  scan: true
  id: bus_i2c
```

_TODO_

- contribute code & test

## IR Ontvanger

```
remote_receiver:
  pin:
    number: GPIO11
    inverted: true
    mode:
      input: true
      pullup: true
  dump: all
```

_TODO_

- test

## Batterij monitor

```

```

_TODO_

- test

## AUX power

```

```

_TODO_

- test

## SD Kaart

```

```

_TODO_

- define use case
