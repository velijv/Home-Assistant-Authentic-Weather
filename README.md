# Home-Assistant-Authentic-Weather
[Authentic Weather](https://www.awwwards.com/authentic-weather-probably-the-most-honest-weather-app.html) phrases to [Home Assistant](https://www.home-assistant.io/) as a sensor and a script for TTS to smart speakers. 

- **phrases.json** - the original wordings by Authentic Weather creators for reference\
- **authentic-weather-sensor.yaml** - a sensor based on Dark Sky icon state\
- **authentic-weather-script.yaml** - a script for text-to-speech to say the current Authentic Weather state out loud. 

To make it work in Google Assistant, make sure you have "**script**" as an exposed domain, or make this particular script exposed to your Google Assistant integration. 

Then you can make a routine to ask "What's the f*cking weather?" to run the script as "Activate Authentic Weather" - which will reply the current weather state, like  `Get your fucking umbrella.` when it's raining. 

***

>
> ## You: _OK Google, what's the f*cking weather?_
> >
> > # <a href="#"><img src="https://img.shields.io/badge/Assistant-responds-4285F4.svg?&logo=GoogleAssistant&logoColor=4285F4&labelColor=fff&theme=flat" height="24" alt="Assistant responds"></a>   _F*cking thunder storm_


<details>
  <summary> 👇 `yaml` </summary>

*** 
  

```yaml
  authentic_weather:
    friendly_name_template: >
        {% set home = states.weather.home.state %} 
        {% if home == 'exceptional' or home == 'sunny' %}
          {{ [ "Fucking love is in the air", "Take off your shirt and get wet", "Time to put on my coolest shades", "Sun fucking glasses", "It's fucking alright today", "Not amazeballs but also not fucking shitty", "Fucking Amaze Balls", "So fucking nice outside, holy schmoly."] | random }}
        {% elif home == 'rainy' %} 
          {{ [ "It's fucking raining", "Get your fucking umbrella", "Shitloads of rain is awaiting you", "It rains cats and dogs", "Meh... Just stay in bed."] | random }} 
        {% elif home == 'snowy' or home == 'snowy-rainy' %} 
          {{ [ "Holy fucking snow", "Are you freezing fucking serious?", "Can't see because fucking snow", "It's fucking skiing time", "Hello? yes, this is snow- man."] | random }} 
        {% elif home == 'windy' %}
          {{ [ "Fucking thunder storm", "It's getting fucking dark", "It's fucking windy", "The storm is coming - May the Force be with you", "Hello? yes, this is snow- man."] | random }}
        {% elif home == 'fog' %} It's fucking foggy.
        {% elif home == 'cloudy' or home == 'partlycloudy' %}
          {{ [ "It's fucking cloudy", "It's just fucking grey", "Fucking fifty shades of grey."] | random }}
        {% elif home == 'partlycloudy' or home == 'clear-night' %}
          {{ [ "Totally not shitty", "It’s like a meh… kinda day."] | random }}
        {% elif home == 'hail' %} HAIL
        {% elif home == 'lightning' %} Fucking thunder storm. 
        {% else %} idk {% endif %} 
    value_template: >-
      {{ state_attr('weather.home','temperature') }}
    unit_of_measurement: "°C"
    icon_template: >-
        {% set home = states.weather.home.state %} 
        {% if home == 'exceptional' or home == 'sunny' %}
          mdi:weather-sunny
        {% elif home == 'rainy' %} 
          mdi:weather-rainy
        {% elif home == 'snowy' or home == 'snowy-rainy' %} 
          mdi:weather-snowy
        {% elif home == 'windy' %}
          mdi:weather-windy
        {% elif home == 'fog' %}
          mdi:weather-fog
        {% elif home == 'cloudy' or home == 'partlycloudy' %}
          mdi:weather-partly-cloudy
        {% elif home == 'partlycloudy' or home == 'clear-night' %}
          mdi:weather-night-partly-cloudy
        {% elif home == 'hail' %}
          mdi:weather-hail
        {% elif home == 'lightning' %}
          mdi:weather-lightning
        {% else %} mdi:balloon {% endif %} 
```
  
</details>

