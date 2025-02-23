# ☀️ Adria-Dashboard-Pup-Up- ☀️

[![Adria-Dashboard-Pup-Up-](https://github.com/user-attachments/assets/c545ab17-c052-4b84-871a-43b32e56e61d)]([https://www.youtube.com/watch?v=Z2pKAX-E4Xw](https://youtu.be/Z2pKAX-E4Xw))
### Dashboard from this video: https://youtu.be/Z2pKAX-E4Xw


### 📥 Installation

Go to your Home Assistant Settings, open the Dashboard-Section and create a new Dashboard.
After that click on the three dots in the top right corner, open the Raw-Configuration and copy the following Code inside.

#### Here is the RAW Code

```yaml
kiosk_mode:
  mobile_settings:
    hide_header: true
background: var(--background-image)
views:
  - title: Adria
    path: balearen
    cards:
      - type: custom:mushroom-chips-card
        chips:
          - type: template
            icon: |-
              {% if is_state("binary_sensor.shelly_blu_dw_weis_door", "on") %}
                mdi:door-open
              {% else %}
                mdi:door-closed-lock
              {% endif %}
            icon_color: |-
              {% if is_state("binary_sensor.nuki_haustur_locked", "on") %}
                red
              {% else %}
                green
              {% endif %}
            tap_action:
              action: more-info
            hold_action:
              action: none
            double_tap_action:
              action: none
            entity: lock.nuki_haustur_lock
          - type: template
            entity: binary_sensor.garagentor_external_input
            icon: >-
              {% if is_state("binary_sensor.garage_tor_magnetschalter", "off")
              %}
                mdi:garage-variant
              {% else %}
                mdi:garage-open-variant
              {% endif %}
            icon_color: |-
              {% if is_state("binary_sensor.garage_tor_magnetschalter", "on") %}
                red
              {% else %}
                green
              {% endif %}
            tap_action:
              action: perform-action
              target:
                entity_id: switch.garage_tor
              perform_action: switch.turn_on
            picture: ''
          - type: template
            icon_color: |-
              {% if is_state("switch.ausen_bewasserung", "on") %}
                blue
              {% endif %}
            entity: switch.ausen_bewasserung
            icon: mdi:water-pump
            tap_action:
              action: toggle
          - type: template
            icon: mdi:shield-home
            entity: automation.alarm_an
            icon_color: |-
              {% if is_state("automation.alarm_an", "on") %}
                green
              {% else %}
                red
              {% endif %}
          - type: template
            entity: switch.alarm
            icon: mdi:alarm-light
            icon_color: |-
              {% if is_state("switch.alarm", "on") %}
                red
              {% endif %}
            tap_action:
              action: toggle
          - type: template
            entity: cover.rollladen_alle
            icon: mdi:blinds-horizontal
            icon_color: none
            tap_action:
              action: more-info
            hold_action:
              action: none
            double_tap_action:
              action: none
          - type: template
            icon_color: ''
            icon: mdi:home-assistant
            tap_action:
              action: navigate
              navigation_path: /lovelace/zentrale-neu
          - type: template
            tap_action:
              action: navigate
              navigation_path: /lovelace/baustelle
            icon: mdi:hammer-screwdriver
        alignment: justify
      - type: horizontal-stack
        cards:
          - type: custom:mushroom-template-card
            primary: ''
            secondary: ''
            icon: ''
            layout: vertical
            picture: '{{state_attr(entity,"entity_picture")}}'
            entity: person.ugur
            badge_icon: |-
              {% if is_state(entity, "not_home") %}
                mdi:home-export-outline
              {% else %} 
                {{state_attr("zone." + states(entity),"icon")}}
              {%- endif %}
            badge_color: >-
              {% if is_state(entity, ["home","home2"]) -%}

              green

              {% elif is_state(entity, "not_home") %}

              red

              {% elif state_attr("zone." + states(entity),"icon") |
              contains('work') %}

              blue

              {%- endif %}
            icon_color: ''
            multiline_secondary: true
            fill_container: true
            tap_action:
              action: more-info
          - type: custom:mushroom-template-card
            primary: ''
            secondary: ''
            icon: ''
            layout: vertical
            picture: '{{state_attr(entity,"entity_picture")}}'
            entity: person.ipo
            badge_icon: |-
              {% if is_state(entity, "not_home") %}
                mdi:home-export-outline
              {% else %} 
                {{state_attr("zone." + states(entity),"icon")}}
              {%- endif %}
            badge_color: >-
              {% if is_state(entity, ["home","home2"]) -%}

              green

              {% elif is_state(entity, "not_home") %}

              red

              {% elif state_attr("zone." + states(entity),"icon") |
              contains('work') %}

              blue

              {%- endif %}
            icon_color: ''
            multiline_secondary: true
            fill_container: true
            tap_action:
              action: more-info
          - type: custom:mushroom-template-card
            primary: ''
            secondary: ''
            icon: ''
            layout: vertical
            picture: '{{state_attr(entity,"entity_picture")}}'
            entity: person.elis
            badge_icon: |-
              {% if is_state(entity, "not_home") %}
                mdi:home-export-outline
              {% else %} 
                {{state_attr("zone." + states(entity),"icon")}}
              {%- endif %}
            badge_color: >-
              {% if is_state(entity, ["home","home2"]) -%}

              green

              {% elif is_state(entity, "not_home") %}

              red

              {% elif state_attr("zone." + states(entity),"icon") |
              contains('work') %}

              blue

              {%- endif %}
            icon_color: ''
            multiline_secondary: true
            fill_container: true
            tap_action:
              action: more-info
          - type: custom:mushroom-template-card
            primary: ''
            secondary: ''
            icon: ''
            layout: vertical
            picture: '{{state_attr(entity,"entity_picture")}}'
            entity: person.elyas
            badge_icon: |-
              {% if is_state(entity, "not_home") %}
                mdi:home-export-outline
              {% else %} 
                {{state_attr("zone." + states(entity),"icon")}}
              {%- endif %}
            badge_color: >-
              {% if is_state(entity, ["home","home2"]) -%}

              green

              {% elif is_state(entity, "not_home") %}

              red

              {% elif state_attr("zone." + states(entity),"icon") |
              contains('work') %}

              blue

              {%- endif %}
            icon_color: ''
            multiline_secondary: true
            fill_container: true
            tap_action:
              action: more-info
          - type: custom:mushroom-template-card
            primary: ''
            icon: mdi:car
            icon_color: >-
              {% if is_state('device_tracker.elektroauto_device_tracker',
              'home') %}
                green
              {% else %}
                red
              {% endif %}
            fill_container: true
            multiline_secondary: true
            layout: vertical
            badge_icon: ''
            badge_color: ''
            picture: ''
            tap_action:
              action: navigate
              navigation_path: '#Auto'
      - type: custom:simple-weather-card
        entity: weather.zuhause
        name: ' '
        backdrop:
          day: var(--primary-color)
          night: '#40445a'
        primary_info:
          - wind_bearing
          - humidity
        secondary_info:
          - precipitation
          - precipitation_probability
        tap_action:
          action: navigate
          navigation_path: '#Wetter'
      - type: vertical-stack
        cards:
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Wohnzimmer
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#Wohnzimmer'
                icon_tap_action:
                  action: call-service
                  service: light.toggle
                  target:
                    entity_id: light.sofa_licht
                secondary: >-
                  {{ states('sensor.thermostat_wohnzimmer_air_temperature') }}
                  °C
                icon: mdi:sofa-outline
                icon_color: |-
                  {% if is_state('light.sofa_licht', 'on') %}
                    orange
                  {% elif is_state('light.sofa_lowboard_licht', 'on') %}
                    orange
                  {% endif %}
              - type: custom:mushroom-template-card
                primary: Terrasse & Außen
                tap_action:
                  action: navigate
                  navigation_path: '#Aussen'
                secondary: '{{ states(''sensor.pluggit_outdoor_t1'') }} °C'
                icon: mdi:fence
                icon_color: |-
                  {% if is_state('switch.pflanzenbeleuchtung', 'on') %}
                    orange
                  {% elif is_state('light.shelly1_e09806967d02', 'on') %}
                    orange
                  {% elif is_state('light.terrasse_led_band', 'on') %}
                    orange
                  {% elif is_state('switch.ausenbeleuchtung_sud', 'on') %}
                    orange
                  {% elif is_state('switch.ausenbeleuchtung_ost', 'on') %}
                    orange
                  {% elif is_state('switch.hofbeleuchtung', 'on') %}
                    orange
                  {% elif is_state('light.tur', 'on') %}
                    orange
                  {% elif is_state('switch.garagenlicht', 'on') %}
                    orange
                  {% elif is_state('light.ausen_uberdachung_licht', 'on') %}
                    orange
                  {% endif %}
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Kochen & Essen
                secondary: '{{ states(''sensor.multi_sensor_kuche_air_temperature'') }} °C'
                icon: mdi:countertop-outline
                icon_color: |-
                  {% if is_state('light.stehleuchte', 'on') %}
                    orange
                  {% elif is_state('light.linienleuchte', 'on') %}
                    orange
                  {% elif is_state('light.kuche_licht', 'on') %}
                    orange
                  {% elif is_state('light.shelly_rgbw_2_channel_4', 'on') %}
                    orange
                  {% elif is_state('light.hue_ensis_down_1', 'on') %}
                    orange
                  {% elif is_state('light.hue_ensis_up_1', 'on') %}
                    orange
                  {% endif %}
                hold_action:
                  action: toggle
                tap_action:
                  action: navigate
                  navigation_path: '#Kochen'
                entity: light.kochleuchte
              - type: custom:mushroom-template-card
                primary: Speisekammer
                tap_action:
                  action: navigate
                  navigation_path: '#Kammer'
                secondary: '{{ states(''sensor.speisekammer_ht_temperature'') }} °C'
                icon: mdi:food-variant
                icon_color: |-
                  {% if is_state('light.speisekammerlicht_2', 'on') %}
                    orange
                  {% endif %}
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: HWR
                secondary: '{{ states(''sensor.hwr_ht_temperature'') }} °C'
                icon: mdi:washing-machine
                icon_color: |-
                  {% if is_state('switch.hwr_licht', 'on') %}
                    orange
                  {% endif %}
                hold_action:
                  action: toggle
                tap_action:
                  action: navigate
                  navigation_path: '#HWR'
                entity: light.kochleuchte
              - type: custom:mushroom-template-card
                primary: WC
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#WC'
                secondary: '{{ states(''sensor.my_air_q_temperatur'') }} °C'
                icon: mdi:toilet
                icon_color: |-
                  {% if is_state('light.wc_licht', 'on') %}
                    orange
                  {% endif %}
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Flur & Garderobe
                entity: sensor.my_air_q_temperatur
                tap_action:
                  action: navigate
                  navigation_path: '#Flur'
                secondary: '{{ states(''sensor.my_air_q_temperatur'') }} °C'
                icon: mdi:stairs
                icon_color: |-
                  {% if is_state('light.garderobe', 'on') %}
                    orange
                  {% elif is_state('light.flur_licht_unten', 'on') %}
                    orange
                  {% elif is_state('light.flur_licht_oben', 'on') %}
                    orange
                  {% endif %}
              - type: custom:mushroom-template-card
                primary: Büro
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#Office'
                secondary: '{{ states(''sensor.buro_wall_display_temperature'') }} °C'
                icon: mdi:chair-rolling
                icon_color: |-
                  {% if is_state('light.buro', 'on') %}
                    orange
                  {% elif is_state('light.buro_neon_led', 'on') %}
                    orange
                  {% elif is_state('switch.schreibtisch_mann_switch_0', 'on') %}
                    blue
                  {% endif %}
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Schlafzimmer
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#Schlafzimmer'
                secondary: >-
                  {{ states('sensor.thermostat_schlafzimmer_air_temperature') }}
                  °C
                icon: mdi:bed-king-outline
                icon_color: |-
                  {% if is_state('switch.schreibtisch_frau', 'on') %}
                    blue
                  {% endif %}
              - type: custom:mushroom-template-card
                primary: Bad
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#Bad'
                secondary: '{{ states(''sensor.thermostat_bad_air_temperature'') }} °C'
                icon: mdi:shower-head
                icon_color: ''
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Elis
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#Elis'
                secondary: '{{ states(''sensor.thermostat_kind_1_air_temperature'') }} °C'
                icon: mdi:draw
                icon_color: |-
                  {% if is_state('light.kinderzimmer_1_bulb_rgbw', 'on') %}
                    orange
                  {% endif %}
              - type: custom:mushroom-template-card
                primary: Elyas
                entity: sensor.durchschnittstemperatur_flur
                tap_action:
                  action: navigate
                  navigation_path: '#Elyas'
                secondary: '{{ states(''sensor.thermostat_kind_2_air_temperature'') }} °C'
                icon: mdi:soccer
                icon_color: |-
                  {% if is_state('light.kinderzimmer_2_bulb_rgbw', 'on') %}
                    orange
                  {% endif %}
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Wohnzimmer'
            name: Wohnzimmer
            show_state: true
            icon: mdi:sofa-outline
            button_type: state
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.thermostat_wohnzimmer_air_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.thermostat_wohnzimmer_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                entity: cover.rollladen_sofa
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 15
                  target:
                    entity_id:
                      - cover.sofa_rollladen
                icon: mdi:roller-shade-closed
                content: ''
              - type: light
                entity: light.ambiente
                content_info: name
                use_light_color: true
                name: Ambiente
                tap_action:
                  action: more-info
              - type: light
                entity: light.kino
                content_info: name
                use_light_color: true
                name: kino
                tap_action:
                  action: more-info
              - type: light
                entity: light.party
                content_info: name
                use_light_color: true
                name: Party
                tap_action:
                  action: more-info
            alignment: justify
          - type: custom:mini-graph-card
            entities:
              - entity: sensor.thermostat_wohnzimmer_air_temperature
                show_state: true
                name: Temperatur
              - entity: sensor.thermostat_wohnzimmer_humidity
                color: green
                show_state: true
                name: Feuchtigkeit
            name: Temperatur & Feuchtigkeit
            hours_to_show: 24
            points_per_hour: 6
            show:
              name: true
              legend: false
              icon: false
              labels: false
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                entity: light.sofa_licht
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
              - type: custom:mushroom-light-card
                entity: light.sofa_lowboard_licht
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                show_color_control: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.sofa_rollladen
                show_buttons_control: true
                show_position_control: true
              - type: custom:mushroom-cover-card
                entity: cover.terrasse_rollladen
                show_position_control: true
                show_buttons_control: true
          - type: media-control
            entity: media_player.spotify
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-media-player-card
                entity: media_player.samsung_tv
                media_controls:
                  - on_off
                show_volume_level: false
                use_media_info: false
                collapsible_controls: false
                layout: horizontal
                fill_container: false
                volume_controls: []
                name: TV
              - type: custom:mushroom-entity-card
                icon: hue:plug
                name: TV
                tap_action:
                  action: more-info
                fill_container: true
                entity: switch.sofa_tv
              - type: custom:mushroom-entity-card
                icon: mdi:soundbar
                name: Soundbar
                tap_action:
                  action: more-info
                fill_container: true
                entity: media_player.soundbar
          - type: vertical-stack
            cards:
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: switch.sofa_steckdose
                    secondary_info: none
                    name: Dose links
                    tap_action:
                      action: toggle
                  - type: custom:mushroom-entity-card
                    entity: switch.sofa_lowboard_steckdose
                    secondary_info: none
                    name: Lowboard
                    tap_action:
                      action: toggle
      - type: custom:mushroom-chips-card
        chips:
          - type: template
            icon_color: |-
              {% if is_state("switch.luftungsanlage","on") %}
                green
              {% else %}
                red
              {% endif %}
            icon: mdi:power
            tap_action:
              action: toggle
            entity: switch.luftungsanlage
          - type: template
            icon: mdi:fan-off
            icon_color: |-
              {% if is_state('sensor.pluggit_fan_level', '0') %}
                blue
              {% endif %}
            tap_action:
              action: call-service
              service: modbus.write_register
              data:
                address: 324
                slave: 255
                value:
                  - 0
                  - 0
                hub: pluggit
              target: {}
          - type: template
            icon: mdi:fan-speed-1
            icon_color: |-
              {% if is_state('sensor.pluggit_fan_level', '1') %}
                blue
              {% endif %}
            tap_action:
              action: call-service
              service: modbus.write_register
              data:
                address: 324
                slave: 255
                value:
                  - 1
                  - 0
                hub: pluggit
              target: {}
          - type: template
            icon: mdi:fan-speed-2
            icon_color: |-
              {% if is_state('sensor.pluggit_fan_level', '2') %}
                blue
              {% endif %}
            tap_action:
              action: call-service
              service: modbus.write_register
              data:
                address: 324
                slave: 255
                value:
                  - 2
                  - 0
                hub: pluggit
              target: {}
          - type: template
            icon: mdi:fan-speed-3
            icon_color: |-
              {% if is_state('sensor.pluggit_fan_level', '3') %}
                blue
              {% endif %}
            tap_action:
              action: call-service
              service: modbus.write_register
              data:
                address: 324
                slave: 255
                value:
                  - 3
                  - 0
                hub: pluggit
              target: {}
          - type: template
            icon: mdi:fan-plus
            icon_color: |-
              {% if is_state('sensor.pluggit_fan_level', '4') %}
                blue
              {% endif %}
            tap_action:
              action: call-service
              service: modbus.write_register
              data:
                address: 324
                slave: 255
                value:
                  - 4
                  - 0
                hub: pluggit
              target: {}
          - type: entity
            entity: sensor.pluggit_filter_remaining_time
            icon: mdi:air-filter
            content_info: state
        alignment: justify
      - type: vertical-stack
        cards:
          - type: horizontal-stack
            cards:
              - type: custom:button-card
                name: Pflanzen & Außen
                icon: mdi:sprout-outline
                color: green
                aspect_ratio: 2.5/1
                tap_action:
                  action: navigate
                  navigation_path: '#Pflanzen'
              - type: custom:button-card
                name: Energie
                icon: mdi:home-battery-outline
                aspect_ratio: 2.5/1
                tap_action:
                  action: navigate
                  navigation_path: '#Energie'
                entity: sensor.powerstream_battery_input_watts
                state:
                  - value: 2
                    operator: '>='
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
                    operator: '='
                    color: pink
                    icon: mdi:home-battery-outline
      - type: vertical-stack
        cards:
          - type: horizontal-stack
            cards:
              - type: custom:button-card
                name: Sicherheit & Kameras
                icon: mdi:cctv
                aspect_ratio: 2.5/1
                color: grey
                tap_action:
                  action: navigate
                  navigation_path: '#Kamera'
              - type: custom:button-card
                name: Roboter
                icon: mdi:robot-mower-outline
                aspect_ratio: 2.5/1
                color: indigo
                tap_action:
                  action: navigate
                  navigation_path: '#Roboter'
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Kamera'
            name: Sicherheit & Kameras
            show_state: true
            icon: mdi:cctv
            button_type: name
            scrolling_effect: false
          - type: custom:bubble-card
            card_type: separator
          - type: alarm-panel
            states:
              - arm_home
              - arm_away
            entity: alarm_control_panel.home_alarm
          - type: custom:bubble-card
            card_type: separator
          - show_state: false
            show_name: false
            camera_view: live
            type: picture-entity
            camera_image: camera.kamera_hof_fliessend
            entity: camera.kamera_hof_fliessend
          - show_state: false
            show_name: false
            camera_view: live
            type: picture-entity
            camera_image: camera.reolink_video_doorbell_poe_sub
            entity: camera.reolink_video_doorbell_poe_sub
          - show_state: false
            show_name: false
            camera_view: live
            type: picture-entity
            entity: camera.kamera_hinten_fliessend
            camera_image: camera.kamera_hinten_fliessend
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Roboter'
            name: Roboter
            show_state: true
            icon: mdi:robot-mower-outline
            button_type: name
            scrolling_effect: false
          - type: custom:bubble-card
            card_type: separator
          - type: custom:mushroom-vacuum-card
            entity: vacuum.roborock_qrevo_curv
            name: Saugrobo
            icon_animation: true
            commands:
              - on_off
              - start_pause
              - stop
              - locate
              - return_home
          - type: custom:mushroom-vacuum-card
            entity: vacuum.saros_10r
            icon: mdi:robot-mower
            name: Rasenrobo
            commands:
              - on_off
              - start_pause
              - stop
              - locate
              - return_home
          - type: custom:bubble-card
            card_type: separator
          - image: default
            image_size: '4'
            show_animation: true
            show_status: true
            show_toolbar: true
            type: custom:landroid-card
            entity: lawn_mower.mower
          - type: custom:vacuum-card
            entity: vacuum.saros_10r
            map: image.saros_10r
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Pflanzen'
            name: Pflanzen & Garten
            show_state: true
            icon: mdi:sprout-outline
            button_type: name
            scrolling_effect: false
          - type: custom:bubble-card
            card_type: separator
          - type: horizontal-stack
            cards:
              - type: custom:bar-card
                title: Zisterne
                name: Füllstand
                icon: mdi:watering-can
                tap_action:
                  action: call-service
                  service: rest_command.messung_zisterne
                  target: {}
                severity:
                  - color: red
                    icon: mdi:water-off-outline
                    from: 0
                    to: 1000
                  - color: Orange
                    icon: mdi:water-alert-outline
                    from: 1001
                    to: 3000
                  - color: lightgreen
                    icon: mdi:water-check
                    from: 3001
                    to: 7000
                entities:
                  - entity: sensor.zisterne_inhalt_in_liter
          - type: custom:bubble-card
            card_type: separator
          - type: vertical-stack
            cards:
              - type: custom:flower-card
                entity: plant.yucca
                battery_sensor: sensor.elefantenfus_battery
                show_bars:
                  - moisture
                  - conductivity
                  - temperature
                  - illuminance
                display_type: full
              - type: custom:flower-card
                entity: plant.cocos
                battery_sensor: sensor.rose_battery
                show_bars:
                  - moisture
                  - conductivity
                  - temperature
                  - illuminance
                display_type: full
          - type: vertical-stack
            cards:
              - type: custom:flower-card
                entity: plant.yucca
                battery_sensor: sensor.elefantenfus_battery
                show_bars:
                  - moisture
                  - conductivity
                  - temperature
                  - illuminance
                display_type: full
              - type: custom:flower-card
                entity: plant.cocos
                battery_sensor: sensor.rose_battery
                show_bars:
                  - moisture
                  - conductivity
                  - temperature
                  - illuminance
                display_type: full
          - type: vertical-stack
            cards:
              - type: custom:flower-card
                entity: plant.yucca
                battery_sensor: sensor.elefantenfus_battery
                show_bars:
                  - moisture
                  - conductivity
                  - temperature
                  - illuminance
                display_type: full
              - type: custom:flower-card
                entity: plant.cocos
                battery_sensor: sensor.rose_battery
                show_bars:
                  - moisture
                  - conductivity
                  - temperature
                  - illuminance
                display_type: full
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Energie'
            name: Energie & Batterien
            show_state: true
            icon: mdi:home-battery-outline
            button_type: name
            scrolling_effect: false
          - type: custom:power-flow-card-plus
            entities:
              battery:
                state_of_charge_unit_white_space: false
                state_of_charge: sensor.electriclevel
                invert_state: true
                entity:
                  production: sensor.outputpackpower
                  consumption: sensor.packinputpower
              grid:
                entity: sensor.fidan_wr_grid_power
              solar:
                display_zero_state: true
                secondary_info:
                  entity: sensor.solarinputpower
                entity: sensor.fidan_wr_ac_power
              fossil_fuel_percentage:
                entity: sensor.co2_signal_grid_fossil_fuel_percentage
                secondary_info:
                  entity: sensor.co2_signal_grid_fossil_fuel_percentage
                  unit_of_measurement: '%'
                display_zero: true
                name: Anteil fossile
                display_zero_state: true
                unit_white_space: false
                use_metadata: false
              home: {}
              individual:
                - entity: sensor.warmepumpe_leistung_total
                  icon: mdi:heat-pump-outline
                  color:
                    - 160
                    - 49
                    - 49
                  color_value: false
                  color_icon: false
                  name: Wärmepumpe
                - entity: sensor.enector_ladeleistung
                  secondary_info:
                    entity: sensor.elektroauto_state_of_charge
                    unit_of_measurement: '%'
                  icon: mdi:ev-station
                  color:
                    - 136
                    - 33
                    - 192
                  display_zero: true
                  name: Wallbox
                  color_value: false
                  color_icon: false
                - entity: sensor.wama_trockner
                  display_zero: true
                  color:
                    - 29
                    - 185
                    - 183
                  color_value: false
                  color_icon: false
                  icon: mdi:tumble-dryer
                  name: Wama & Trockner
                - entity: sensor.kuche_spulmaschine_power
                  display_zero: true
                  color:
                    - 55
                    - 144
                    - 86
                  name: Spülmaschine
                  icon: mdi:dishwasher
            clickable_entities: true
            display_zero_lines:
              mode: show
              transparency: 50
              grey_color:
                - 189
                - 189
                - 189
            use_new_flow_rate_model: true
            w_decimals: 0
            kw_decimals: 1
            min_flow_rate: 2
            max_expected_power: 2000
            min_expected_power: 0.01
            watt_threshold: 1000
            transparency_zero_lines: 0
            disable_dots: false
            max_flow_rate: 10
            dashboard_link: /energy
            dashboard_link_label: Ab zum Energie-Dashboard
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
              - entity: sensor.multi_sensor_flur_battery_level
              - entity: sensor.multi_sensor_kuche_battery_level
              - entity: sensor.hue_wall_switch_module_1_battery
              - entity: sensor.garderobe_bewegungsmelder_battery
              - entity: sensor.nuki_haustur_battery
              - entity: sensor.nuki_hutte_battery
              - entity: sensor.elefantenfus_battery
              - entity: sensor.rose_battery
              - entity: sensor.aussenfuhler_battery
              - entity: sensor.fibaro_door_window_sensor_2_battery_level
              - entity: sensor.shelly_blu_dw_schwarz_battery
              - entity: sensor.shelly_blu_dw_schwarz_battery
              - entity: sensor.shelly_blu_dw_weis_battery
              - entity: sensor.fibaro_door_window_sensor_2_battery_level
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Aussen'
            name: Terrasse & Außen
            show_state: true
            icon: mdi:fence
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - show_state: true
                show_background: false
                show_icon: true
                entity: sensor.pluggit_outdoor_t1
                icon: mdi:home-thermometer-outline
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 15
                  target:
                    entity_id: cover.terrasse_rollladen
                icon: mdi:roller-shade-closed
                content: ''
              - type: template
                double_tap_action:
                  action: none
                icon: >-
                  {% if
                  is_state("binary_sensor.turkontakt_terrasse_window_door_is_open"
                  , "off") %}
                    mdi:door-sliding
                  {% else %}
                    mdi:door-sliding-open
                  {% endif %}
                icon_color: >-
                  {% if
                  is_state("binary_sensor.turkontakt_terrasse_window_door_is_open"
                  , "off") %}
                    green
                  {% else %}
                    red
                  {% endif %}
                tap_action:
                  action: none
                hold_action:
                  action: none
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                entity: light.shelly1_e09806967d02
                icon: mdi:wall-sconce-flat
              - type: custom:mushroom-light-card
                entity: light.terrasse_led_band
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                show_color_control: true
                icon: mdi:led-strip-variant
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.terrasse_rollladen
                show_position_control: true
                show_buttons_control: true
          - type: vertical-stack
            cards:
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    secondary_info: none
                    name: Steckdose Terrasse
                    icon: mdi:power-socket-eu
                    tap_action:
                      action: toggle
                    icon_color: accent
                    entity: switch.terrasse_steckdose
                  - type: custom:mushroom-entity-card
                    entity: light.tur
                    secondary_info: none
                    name: Haustür
                    tap_action:
                      action: toggle
                    icon: hue:wall-resonate
                    icon_color: accent
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: light.shelly1_e8db84a936bd
                    secondary_info: none
                    icon: hue:wall-resonate
                    name: Süd
                    tap_action:
                      action: toggle
                    icon_color: accent
                  - type: custom:mushroom-entity-card
                    entity: light.shelly1_e8db84d665c7
                    secondary_info: none
                    icon: hue:wall-resonate
                    name: Ost
                    tap_action:
                      action: toggle
                    icon_color: accent
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: light.shelly1_e8db84803a41_2
                    secondary_info: none
                    name: Hof
                    icon: hue:go-group
                    tap_action:
                      action: toggle
                    icon_color: accent
                  - type: custom:mushroom-entity-card
                    entity: light.shelly1_c45bbe6af1e0
                    secondary_info: none
                    icon: hue:go-group
                    name: Pflanzen
                    tap_action:
                      action: toggle
                    icon_color: accent
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: light.shelly1mini_6055f998e204_switch_0
                    secondary_info: none
                    name: Garagenlicht
                    icon: mdi:garage-variant
                    tap_action:
                      action: toggle
                    icon_color: accent
                  - type: custom:mushroom-entity-card
                    secondary_info: none
                    icon: mdi:led-strip
                    name: Überdachung
                    tap_action:
                      action: toggle
                    icon_color: accent
                    entity: light.ausen_uberdachung_licht
              - type: horizontal-stack
                cards: []
          - type: entity
            entity: sensor.garage_hyper_2000_power
            icon: mdi:solar-power-variant
          - type: custom:bar-card
            title: Zisterne
            name: .
            icon: mdi:watering-can
            tap_action:
              action: call-service
              service: rest_command.messung_zisterne
              target: {}
            severity:
              - color: red
                icon: mdi:water-off-outline
                from: 0
                to: 1000
              - color: Orange
                icon: mdi:water-alert-outline
                from: 1001
                to: 3000
              - color: lightgreen
                icon: mdi:water-check
                from: 3001
                to: 7000
            entities:
              - entity: sensor.zisterne_inhalt_in_liter
          - type: custom:mini-graph-card
            entities:
              - entity: sensor.garage_tor_temperature
                show_state: true
                name: Temperatur
              - entity: sensor.garage_tor_humidity
                color: green
                show_state: true
                name: Feuchtigkeit
            name: Garage
            hours_to_show: 24
            points_per_hour: 6
            show:
              name: true
              legend: false
              icon: false
              labels: false
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Kochen'
            name: Kochen & Essen
            show_state: true
            icon: mdi:countertop-outline
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.multi_sensor_kuche_air_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.my_air_q_luftfeuchtigkeit
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                entity: cover.rollladen_sofa
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 15
                  target:
                    entity_id:
                      - cover.kuche_rollladen
                      - cover.esstisch_rollladen_links
                      - cover.esstisch_rollladen_rechts
                icon: mdi:roller-shade-closed
                content: ''
            alignment: justify
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                icon: hue:ensis
                show_brightness_control: true
                collapsible_controls: true
                tap_action:
                  action: toggle
                name: Unterlicht
                show_color_temp_control: true
                use_light_color: true
                entity: light.hue_ensis_down_1
              - type: custom:mushroom-light-card
                name: Oberlicht
                icon: hue:ensis-up
                use_light_color: true
                show_brightness_control: true
                collapsible_controls: true
                show_color_temp_control: true
                tap_action:
                  action: toggle
                hold_action:
                  action: more-info
                entity: light.hue_ensis_up_1
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                icon: hue:centura-round
                show_brightness_control: true
                collapsible_controls: true
                tap_action:
                  action: toggle
                name: Beleuchtung
                show_color_control: false
                show_color_temp_control: false
                use_light_color: false
                entity: light.kuche_licht
              - type: custom:mushroom-light-card
                entity: light.esstisch_stehleuchte
                use_light_color: true
                show_brightness_control: true
                collapsible_controls: true
                show_color_control: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                entity: light.esstisch_linienleuchte
                icon: mdi:led-strip
                use_light_color: true
                show_brightness_control: true
                show_color_control: true
                collapsible_controls: true
                name: Paneellicht
              - type: custom:mushroom-light-card
                entity: light.shelly_rgbw_2_channel_4
                name: Hängeschrank
                icon: mdi:led-strip
                use_light_color: true
                show_brightness_control: true
                collapsible_controls: true
                show_color_temp_control: false
                show_color_control: false
                tap_action:
                  action: toggle
                hold_action:
                  action: more-info
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.esstisch_rolllladen_links
                show_buttons_control: true
                show_position_control: true
              - type: custom:mushroom-cover-card
                entity: cover.esstisch_rollladen_rechts
                show_position_control: true
                show_buttons_control: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.kuche_rollladen
                show_buttons_control: true
                show_position_control: true
              - type: custom:mushroom-cover-card
                entity: cover.terrasse_rollladen
                show_position_control: true
                show_buttons_control: true
          - type: vertical-stack
            cards:
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: switch.kuche_spulmaschine
                    secondary_info: none
                    name: Spülmaschine
                    tap_action:
                      action: toggle
                  - type: custom:mushroom-entity-card
                    entity: switch.kuche_spulmaschine
                    secondary_info: none
                    name: Schrank
                    tap_action:
                      action: toggle
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Office'
            name: Büro
            show_state: true
            icon: mdi:chair-rolling
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.buro_wall_display_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.buro_wall_display_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                entity: cover.rollladen_sofa
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 24
                  target:
                    entity_id: cover.buro_rollladen
                icon: mdi:roller-shade-closed
                content: ''
            alignment: justify
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                icon: mdi:ceiling-light
                show_brightness_control: false
                collapsible_controls: true
                tap_action:
                  action: toggle
                name: Beleuchtung
                show_color_control: false
                show_color_temp_control: false
                use_light_color: false
                entity: light.shellyplus1pm_a8032abbdaa0_switch_0
              - type: custom:mushroom-light-card
                collapsible_controls: true
                name: Neon
                show_brightness_control: true
                use_light_color: true
                show_color_control: true
                icon: hue:lightstrip
                show_color_temp_control: false
                entity: light.buro_neon_led
              - type: custom:mushroom-light-card
                entity: light.key_light
                show_brightness_control: true
                use_light_color: false
                show_color_temp_control: true
                collapsible_controls: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                show_position_control: true
                show_tilt_position_control: false
                show_buttons_control: true
                entity: cover.buro_rollladen
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Schreibtisch
                secondary: |
                  {{states('sensor.schreibtisch_mann_power') }} W
                icon: mdi:desk
                entity: switch.schreibtisch_mann_switch_0
                icon_color: |-
                  {% if is_state("switch.schreibtisch_mann_switch_0", "on") %}
                    orange
                  {% endif %}
          - type: entities
            entities:
              - entity: sensor.ams_1_humidity
                name: AMS 1
              - entity: sensor.ams_1_humidity
                name: AMS 2
              - entity: sensor.ams_1_humidity
                name: AMS 3
          - type: custom:ha-bambulab-skipobject-card
            entity: sun.sun
            printer: 02e2753814e32d06af07f89764fcfc74
          - type: custom:ha-bambulab-ams-card
            entity: ''
            header: ''
            subtitle: ''
            style: vector
            ams: f709e4b346bb9496a8697577843e9e10
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Wetter'
            name: Wetter
            show_state: true
            icon: mdi:weather-sunny-alert
            button_type: name
            scrolling_effect: false
          - type: custom:weather-chart-card
            entity: weather.zuhause
            show_main: true
            show_temperature: true
            show_current_condition: true
            show_attributes: true
            show_time: true
            show_time_seconds: true
            show_day: true
            show_date: true
            show_humidity: true
            show_pressure: false
            show_wind_direction: false
            show_wind_speed: true
            show_sun: true
            show_feels_like: false
            show_dew_point: false
            show_wind_gust_speed: false
            show_visibility: false
            show_last_changed: false
            use_12hour_format: false
            icons_size: '50'
            animated_icons: true
            icon_style: style1
            autoscroll: true
            forecast:
              precipitation_type: rainfall
              show_probability: false
              labels_font_size: '11'
              precip_bar_size: '90'
              style: style2
              show_wind_forecast: true
              condition_icons: true
              round_temp: false
              type: daily
              number_of_forecasts: '7'
              disable_animation: false
            units:
              speed: ''
          - type: iframe
            url: >-
              https://radar.wo-cloud.com/mobile/rr/interactive?wrx=48.46,8.4&wrm=7.49&wry=48.81,8.32
            aspect_ratio: 100%
          - type: custom:weather-radar-card
            zoom_level: 10
            map_style: Voyager
            show_playback: true
            show_zoom: true
            show_scale: false
            show_marker: false
            static_map: false
            show_range: false
            square_map: false
            show_recenter: true
            extra_labels: false
          - type: custom:clock-weather-card
            entity: weather.zuhause
            title: Daheim
            sun_entity: sun.sun
            temperature_sensor: sensor.ausenfuhler_temperature
            humidity_sensor: sensor.ausenfuhler_humidity
            weather_icon_type: line
            animated_icon: true
            forecast_rows: 14
            locale: de
            time_pattern: HH:mm
            time_format: 24
            date_pattern: ccc, d.MM.yy
            hide_today_section: false
            hide_forecast_section: false
            show_humidity: true
            hide_clock: false
            hide_date: false
            hourly_forecast: false
            use_browser_time: false
            time_zone: null
            show_decimal: true
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Flur'
            name: Flur & Garderobe
            show_state: true
            icon: mdi:stairs
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.my_air_q_temperatur
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.cocos_air_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                entity: cover.flur_rollladen
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 15
                  target:
                    entity_id:
                      - cover.flur_rollladen
                icon: mdi:roller-shade-closed
                content: ''
              - type: template
                tap_action:
                  action: call-service
                  service: script.toggle
                  target:
                    entity_id: script.klavierzeit
                icon: mdi:piano
                icon_color: |-
                  {% if is_state("automation.spiegellicht_an", "on") %}
                    black
                  {% else %}
                    red
                  {% endif %}
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                entity: light.flur_licht_unten
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
              - type: custom:mushroom-light-card
                entity: light.flur_licht_oben
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                show_color_control: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                entity: light.flur_spiegel_licht
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
              - type: custom:mushroom-light-card
                entity: light.garderobe
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                show_color_control: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.flur_rollladen
                show_buttons_control: true
                show_position_control: true
          - type: vertical-stack
            cards:
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: switch.alarm
                    secondary_info: none
                    name: Alarm
                    tap_action:
                      action: toggle
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Bad'
            name: Bad
            show_state: true
            icon: mdi:shower-head
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.thermostat_bad_air_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.thermostat_bad_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 30
                  target:
                    entity_id:
                      - cover.bad_rollladen_links
                      - cover.bad_rollladen_rechts
                icon: mdi:roller-shade-closed
                content: ''
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.bad_rollladen_links
                show_buttons_control: true
                show_position_control: true
              - type: custom:mushroom-cover-card
                entity: cover.bad_rollladen_rechts
                show_position_control: true
                show_buttons_control: true
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Schlafzimmer'
            name: Schlafzimmer
            show_state: true
            icon: mdi:bed-king-outline
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.thermostat_schlafzimmer_air_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.thermostat_schlafzimmer_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                entity: cover.schlafzimmer_rollladen
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 15
                  target:
                    entity_id:
                      - cover.schlafzimmer_rollladen
                icon: mdi:roller-shade-closed
                content: ''
            alignment: justify
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.schlafzimmer_rollladen
                show_buttons_control: true
                show_position_control: true
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-template-card
                primary: Schreibtisch
                secondary: |
                  {{states('sensor.schreibtisch_frau_power') }} W
                icon: mdi:desk
                icon_color: |-
                  {% if is_state("switch.schreibtisch_frau", "on") %}
                    orange
                  {% endif %}
                tap_action:
                  action: toggle
                entity: switch.schreibtisch_frau
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Elis'
            name: Elis
            show_state: true
            icon: mdi:draw
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.thermostat_kind_1_air_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.thermostat_kind_1_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 20
                  target:
                    entity_id:
                      - cover.kinderzimmer_1_rollladen_links
                      - cover.kinderzimmer_1_rollladen_rechts
                icon: mdi:roller-shade-closed
                content: ''
          - type: custom:mushroom-light-card
            name: Licht
            icon: hue:ceiling-fair
            use_light_color: false
            show_brightness_control: false
            collapsible_controls: true
            show_color_temp_control: false
            show_color_control: false
            tap_action:
              action: toggle
            hold_action:
              action: more-info
            entity: light.kinderzimmer_1_bulb_rgbw
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.kinderzimmer_1_rollladen_links
                show_buttons_control: true
                show_position_control: true
              - type: custom:mushroom-cover-card
                entity: cover.kinderzimmer_1_rollladen_rechts
                show_position_control: true
                show_buttons_control: true
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Elyas'
            name: Elyas
            show_state: true
            icon: mdi:soccer
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.thermostat_kind_2_air_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.thermostat_kind_2_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 20
                  target:
                    entity_id:
                      - cover.kinderzimmer_2_rollladen_links
                      - cover.kinderzimmer_2_rollladen_rechts
                icon: mdi:roller-shade-closed
                content: ''
          - type: custom:mushroom-light-card
            name: Licht
            icon: hue:ceiling-fair
            use_light_color: false
            show_brightness_control: false
            collapsible_controls: true
            show_color_temp_control: false
            show_color_control: false
            tap_action:
              action: toggle
            hold_action:
              action: more-info
            entity: light.kinderzimmer_2_bulb_rgbw
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.kinderzimmer_2_rollladen_links
                show_buttons_control: true
                show_position_control: true
              - type: custom:mushroom-cover-card
                entity: cover.kinderzimmer_2_rollladen_rechts
                show_position_control: true
                show_buttons_control: true
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#Kammer'
            name: Kammer
            show_state: true
            icon: mdi:broom
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.speisekammer_ht_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.speisekammer_ht_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                entity: light.speisekammer_licht
                name: Kammer
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                icon: mdi:light-recessed
          - type: vertical-stack
            cards:
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: switch.speisekammer_gerate
                    secondary_info: none
                    name: Speisekammer Geräte
                    icon: mdi:power-socket-eu
                    tap_action:
                      action: toggle
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            entity: sensor.thermostat_wohnzimmer_air_temperature
            hash: '#Auto'
            name: Auto
            show_state: true
            icon: mdi:car-sports
            button_type: name
            scrolling_effect: false
          - type: picture-elements
            elements:
              - type: state-badge
                entity: sensor.elektroauto_state_of_charge
                style:
                  top: 75%
                  left: 2%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: sensor.elektroauto_range_electric
                style:
                  top: 75%
                  left: 15%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: binary_sensor.elektroauto_tire_warning
                style:
                  top: 75%
                  left: 28%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: binary_sensor.elektroauto_low_brake_fluid_warning
                style:
                  top: 75%
                  left: 41%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: binary_sensor.elektroauto_low_wash_water_warning
                style:
                  top: 75%
                  left: 54%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: sensor.nt_e_1194e_tire_pressure_front_right
                style:
                  top: 46%
                  left: 25%
                  transform: scale(0.7,0.7)
                  color: rgba(0,0,0,0)
              - type: state-badge
                entity: sensor.nt_e_1194e_tire_pressure_front_left
                style:
                  top: 50%
                  left: 38%
                  transform: scale(0.7,0.7)
                  color: rgba(0,0,0,0)
              - type: state-badge
                entity: sensor.nt_e_1194e_tire_pressure_rear_left
                style:
                  top: 48%
                  left: 71%
                  transform: scale(0.7,0.7)
                  color: rgba(0,0,0,0)
              - type: state-badge
                entity: sensor.nt_e_1194e_tire_pressure_rear_right
                style:
                  top: 45%
                  left: 58%
                  transform: scale(0.7,0.7)
                  color: rgba(0,0,0,0)
              - type: state-icon
                entity: button.nt_e_1194e_preclimate_start
                icon: mdi:radiator
                style:
                  top: 25%
                  left: 44%
                  transform: scale(3,3)
                tap_action:
                  action: call-service
                  service: button.press
                  service_data:
                    entity_id: button.nt_e_1194e_preclimate_start
              - type: state-icon
                entity: button.nt_e_1194e_preclimate_stop
                icon: mdi:radiator-off
                style:
                  top: 25%
                  left: 69%
                  transform: scale(3,3)
                tap_action:
                  action: call-service
                  service: button.press
                  service_data:
                    entity_id: button.nt_e_1194e_preclimate_stop
              - type: state-icon
                entity: lock.elektroauto_lock
                icon: mdi:lock
                style:
                  top: 10%
                  left: 5%
                  transform: scale(3,3)
                tap_action:
                  action: more-info
            image: /local/mercedes-eqb-2021.jpg
          - type: picture-elements
            elements:
              - type: state-badge
                entity: sensor.elektroauto_state_of_charge
                style:
                  top: 80%
                  left: 2%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: sensor.elektroauto_range_electric
                style:
                  top: 80%
                  left: 15%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: binary_sensor.elektroauto_tire_warning
                style:
                  top: 80%
                  left: 28%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: binary_sensor.elektroauto_low_brake_fluid_warning
                style:
                  top: 80%
                  left: 41%
                  transform: scale(0.8,0.8)
              - type: state-badge
                entity: binary_sensor.elektroauto_low_wash_water_warning
                style:
                  top: 80%
                  left: 54%
                  transform: scale(0.8,0.8)
              - type: state-icon
                entity: lock.elektroauto_lock
                icon: mdi:lock
                style:
                  top: 10%
                  left: 5%
                  transform: scale(3,3)
                tap_action:
                  action: more-info
            image: /local/ID7.jpeg
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#HWR'
            name: HWR
            show_state: true
            icon: mdi:broom
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - entity: sensor.hwr_ht_temperature
                show_state: true
                show_background: false
                show_icon: true
              - entity: sensor.hwr_ht_humidity
                show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 30
                  target:
                    entity_id: cover.hwr_rollladen
                icon: mdi:roller-shade-closed
                content: ''
              - type: entity
                entity: sensor.pluggit_supply_t2
                icon: mdi:home
              - type: entity
                entity: sensor.pluggit_outdoor_t1
                icon: mdi:thermometer
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                entity: light.shelly1pmmini_6055f99ff608_switch_0
                name: HWR Licht
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                icon: mdi:light-recessed
          - type: vertical-stack
            cards:
              - type: custom:mushroom-cover-card
                entity: cover.hwr_rollladen
                name: HWR
                icon: ''
                show_position_control: true
                show_buttons_control: true
                tap_action:
                  action: more-info
                fill_container: false
                show_tilt_position_control: false
          - type: history-graph
            entities:
              - entity: sensor.warmepumpe_leistung_total
            hours_to_show: 2
          - type: vertical-stack
            cards:
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: switch.hwr_waschmaschine
                    secondary_info: none
                    name: Waschmaschine
                    icon: mdi:washing-machine
                    tap_action:
                      action: toggle
                  - type: custom:mushroom-entity-card
                    entity: switch.hwr_trockner
                    secondary_info: none
                    name: Trockner
                    icon: mdi:tumble-dryer
                    tap_action:
                      action: toggle
              - type: horizontal-stack
                cards:
                  - type: custom:mushroom-entity-card
                    entity: switch.luftungsanlage
                    secondary_info: none
                    icon: mdi:air-purifier
                    tap_action:
                      action: toggle
      - type: vertical-stack
        cards:
          - type: custom:bubble-card
            card_type: pop-up
            hash: '#WC'
            name: WC
            show_state: true
            icon: mdi:broom
            button_type: name
            show_attribute: false
            show_header: true
            scrolling_effect: false
            tap_action:
              action: call-service
              service: light.toggle
              data: {}
              target: {}
            button_action:
              tap_action:
                action: call-service
                service: light.toggle
                data: {}
                target: {}
            sub_button:
              - show_state: true
                show_background: false
                show_icon: true
                entity: sensor.my_air_q_temperatur
              - show_state: true
                show_icon: true
                show_background: false
                show_name: false
                show_attribute: false
                show_last_changed: false
                entity: sensor.my_air_q_luftfeuchtigkeit
          - type: custom:mushroom-chips-card
            chips:
              - type: template
                tap_action:
                  action: call-service
                  service: cover.set_cover_position
                  data:
                    position: 30
                  target:
                    entity_id: cover.hwr_rollladen
                icon: mdi:roller-shade-closed
                content: ''
          - type: horizontal-stack
            cards:
              - type: custom:mushroom-light-card
                name: WC Licht
                fill_container: false
                show_brightness_control: true
                collapsible_controls: true
                icon: mdi:light-recessed
                entity: light.wc_licht
    background: {}
    layout:
      width: 1
      max_cols: 1
```
