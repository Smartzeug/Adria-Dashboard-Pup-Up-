# ☀️ Adria-Dashboard-Pop-Up ☀️

![Screenshot 23 02 2025 um 20 37 20 PM](https://github.com/user-attachments/assets/db0cccf5-f125-4e73-8aa4-2dbb7a28fd9a)


### Dashboard von diesem Video: [https://youtu.be/Z2pKAX-E4Xw](https://youtu.be/Z2pKAX-E4Xw)

### Eingesetzte Repositories
Bar Card - https://github.com/custom-cards/bar-card
Bubble Card - https://github.com/Clooos/Bubble-Card
Button Card - https://github.com/custom-cards/button-card
Deutscher Wetterdienst - https://github.com/FL550/dwd_weather
Kiosk Mode - https://github.com/NemesisRE/kiosk-mode
Mini Graph Card - https://github.com/kalkih/mini-graph-card
Mushroom - https://github.com/piitaya/lovelace-mushroom
Simple Weather Card - https://github.com/kalkih/simple-weather-card
Weather Chart Card - https://github.com/mlamberts78/weather-chart-card
Weather Radar Card - https://github.com/Makin-Things/weather-radar-card

### Mushroom Chips

Symbol
```
{% if is_state("binary_sensor.DeinGaragentor_magnetschalter", "off") %}
  mdi:garage-variant
{% else %}
  mdi:garage-open-variant
{% endif %}
```

Icon-Farbe
```
{% if is_state("binary_sensor.DeinGaragentor_magnetschalter", "on") %}
  red
{% else %}
  green
{% endif %}
```

Etwas schalten
```
    tap_action:
      action: perform-action
      target:
        entity_id: switch.DeinGaragentor
      perform_action: switch.turn_on
```

### Mushroom Template für Personen / Auto

Badge-Icon
```
{% if is_state(entity, "not_home") %}
  mdi:home-export-outline
{% else %} 
  {{state_attr("zone." + states(entity),"icon")}}
{%- endif %}
```

Badge-Farbe
```
{% if is_state(entity, ["home"]) -%}
green
{% elif is_state(entity, "not_home") %}
red
{%- endif %}
```

Bild (ersetzt das Icon)
```
{{state_attr(entity,"entity_picture")}}
```

Bei Auto
Icon-Farbe
```
{% if is_state('device_tracker.DeinElektroauto_device_tracker', 'home') %}
  green
{% else %}
  red
{% endif %}
```

### Mushroom Template für Räume

Icon-Farbe
```
{% if is_state('light.DeinLicht1', 'on') %}
  orange
{% elif is_state('light.DeinLicht2', 'on') %}
  orange
{% endif %}
```

Sekundäre Information
```
{{ states('sensor.DeinThermostat') }} °C
```

### Button Card 
```
type: custom:button-card
name: Pflanzen & Außen
icon: mdi:sprout-outline
color: green
aspect_ratio: 2.5/1
tap_action:
  action: navigate
  navigation_path: "#DeinRaum"
```



### Button Card mit blinken
```
type: custom:button-card
name: Energie
icon: mdi:home-battery-outline
aspect_ratio: 2.5/1
tap_action:
  action: navigate
  navigation_path: "#DeinRaum"
entity: sensor.DeinSensor
state:
  - value: 2
    operator: ">="
    color: orange
    icon: mdi:home-battery-outline
    styles:
      card:
        - animation: blink 2.5s ease infinite
  - value: 1
    operator: <=
    color: teal
    icon: mdi:home-battery-outline
    styles:
      card:
        - animation: blink 2.5s ease infinite
  - value: 0
    operator: "="
    color: pink
    icon: mdi:home-battery-outline
```

### Simple Weather Card
```
type: custom:simple-weather-card
entity: weather.DeinWetterSensor
name: " "
backdrop:
  day: var(--primary-color)
  night: "#40445a"
primary_info:
  - wind_bearing
  - humidity
secondary_info:
  - precipitation
  - precipitation_probability
tap_action:
  action: navigate
  navigation_path: "#Wetter"
```

### Bar Card
```
type: vertical-stack
cards:
  - type: custom:bar-card
    title: Batterien
    severity:
      - color: red
        icon: mdi:battery-alert-variant-outline
        from: 0
        to: 25
      - color: Orange
        icon: mdi:battery-50
        from: 26
        to: 50
      - color: green
        icon: mdi:battery
        from: 51
        to: 100
    entities:
      - entity: sensor.DeineBatterie1
      - entity: sensor.DeineBatterie2
      - entity: sensor.DeineBatterie3
```

### Kiosk Mode auf dem Smartphone
```
kiosk_mode:
  mobile_settings:
    hide_header: true
```
