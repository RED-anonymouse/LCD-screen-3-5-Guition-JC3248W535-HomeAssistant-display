
# 3,5" Guition JC3248W535 HomeAssistant display

There are many more or less complex designs for this display. However, I wanted a simple screen showing the temperature and humidity of the room it is located in, the outside temperature, the forecast, and the time. I couldn't find anything like that, so I created this design. In addition, I added pages with light switches for a given room and a list of data from several indicators. 

Backlight management has been added to the logic. During the day, the backlight is set to 30%, and at night it automatically switches to 15%. When interaction is detected, it will brighten to 100%. Also, switching pages when there is no interaction will return to the initial state, i.e. to the temperature page.  

## App screenshots
<img src="https://github.com/user-attachments/assets/e580e1c0-858c-4c4d-9b5e-483f64693d2c" width="300">
<img src="https://github.com/user-attachments/assets/05ee25ea-9151-4c15-908f-950be87b4b4a" width="300">
<img src="https://github.com/user-attachments/assets/0e92f17f-f48f-451a-94d7-0c84518f44ff" width="300">

## Case screenshots
<img src="https://github.com/user-attachments/assets/6758cd0f-71b5-47a5-a005-a55db29a830f" width="300">
<img src="https://github.com/user-attachments/assets/3cbbee5b-55ad-44cd-8ec5-7ab7fd986809" width="300">

# Instal
Remember to download the font with icons and add it to the ESPhome folder on your Home Assistant <br> (https://github.com/Templarian/MaterialDesign-Webfont/blob/master/fonts/materialdesignicons-webfont.ttf),<br> and create additional entities for each day of the weather forecast.
```
template:
   # --- FORECAST (TRIGGER) ---
  - trigger:
      - trigger: time_pattern
        minutes: "/30"  # Odświeżanie co 30 minut
      - trigger: homeassistant
        event: start    # Oraz przy starcie systemu
    action:
      - action: weather.get_forecasts
        target:
          entity_id: weather.forecast_dom
        data:
          type: daily
        response_variable: w_forecast
    sensor:
      # --- DAY 0 ---
      - name: "Weather Forecast Dom High Temp 0"
        unique_id: weather_forecast_dom_high_temp_0
        state: "{{ w_forecast['weather.forecast_dom'].forecast[0].temperature }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Low Temp 0"
        unique_id: weather_forecast_dom_low_temp_0
        state: "{{ w_forecast['weather.forecast_dom'].forecast[0].templow }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Condition 0"
        unique_id: weather_forecast_dom_condition_0
        state: "{{ w_forecast['weather.forecast_dom'].forecast[0].condition }}"

      # --- DAY 1 ---
      - name: "Weather Forecast Dom High Temp 1"
        unique_id: weather_forecast_dom_high_temp_1
        state: "{{ w_forecast['weather.forecast_dom'].forecast[1].temperature }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Low Temp 1"
        unique_id: weather_forecast_dom_low_temp_1
        state: "{{ w_forecast['weather.forecast_dom'].forecast[1].templow }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Condition 1"
        unique_id: weather_forecast_dom_condition_1
        state: "{{ w_forecast['weather.forecast_dom'].forecast[1].condition }}"

      # --- DAY 2 ---
      - name: "Weather Forecast Dom High Temp 2"
        unique_id: weather_forecast_dom_high_temp_2
        state: "{{ w_forecast['weather.forecast_dom'].forecast[2].temperature }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Low Temp 2"
        unique_id: weather_forecast_dom_low_temp_2
        state: "{{ w_forecast['weather.forecast_dom'].forecast[2].templow }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Condition 2"
        unique_id: weather_forecast_dom_condition_2
        state: "{{ w_forecast['weather.forecast_dom'].forecast[2].condition }}"

      # --- DAY 3 ---
      - name: "Weather Forecast Dom High Temp 3"
        unique_id: weather_forecast_dom_high_temp_3
        state: "{{ w_forecast['weather.forecast_dom'].forecast[3].temperature }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Low Temp 3"
        unique_id: weather_forecast_dom_low_temp_3
        state: "{{ w_forecast['weather.forecast_dom'].forecast[3].templow }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Condition 3"
        unique_id: weather_forecast_dom_condition_3
        state: "{{ w_forecast['weather.forecast_dom'].forecast[3].condition }}"

      # --- DAY 4 ---
      - name: "Weather Forecast Dom High Temp 4"
        unique_id: weather_forecast_dom_high_temp_4
        state: "{{ w_forecast['weather.forecast_dom'].forecast[4].temperature }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Low Temp 4"
        unique_id: weather_forecast_dom_low_temp_4
        state: "{{ w_forecast['weather.forecast_dom'].forecast[4].templow }}"
        unit_of_measurement: "°C"
      - name: "Weather Forecast Dom Condition 4"
        unique_id: weather_forecast_dom_condition_4
        state: "{{ w_forecast['weather.forecast_dom'].forecast[4].condition }}"
```
The next step will be to change all the entities that you will use on your screen.

## Files for printing the casing
https://drive.google.com/file/d/1Q2JvgJPOE6jzsvzelRSTnS5tt993zZ0X/view?usp=drive_link <br>
https://drive.google.com/file/d/1GalZ0HC4w-Q2IZYL-O6ipnsnNJTMi7es/view?usp=drive_link

## Badges

Add badges from somewhere like: [shields.io](https://shields.io/)

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)


## Contributing

Contributions are always welcome!

See `contributing.md` for ways to get started.

Please adhere to this project's `code of conduct`.

