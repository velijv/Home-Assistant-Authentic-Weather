# Home-Assistant-Authentic-Weather
[Authentic Weather](http://authenticweather.com/) phrases to [Home Assistant](https://www.home-assistant.io/) as a sensor and a script for TTS to smart speakers. 

**phrases.json** - the original wordings by Authentic Weather creators for reference\
**authentic-weather-sensor.yaml** - a sensor based on Dark Sky icon state\
**authentic-weather-script.yaml** - a script for text-to-speech to say the current Authentic Weather state out loud. 

To make it work in Google Assistant, make sure you have "script" as an exposed domain, or make this particular script exposed to your Google Assistant integration. 
Then you can make a routine to ask "What's the f*cking weather?" to run the script as "Activate Authentic Weather" - which will reply the current weather state, like "Get your fucking umbrella." when it's raining. 

# "OK Google, what's the f*cking weather?"
# "F*cking thunder storm."
