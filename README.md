# kindle-weather-dashboard

My customized version of a simple webpage with weather information.

# Try it!

Original version at: http://kindle.hrincar.eu/weather/ and that's it!

This version includes my own modifications and may remove some of the original code over time.

_Please, if you use this website, generate your free OWM token (see: https://openweathermap.org/api for more info), because the default token can be blocked and changed at any time and the weather forecast can stop working._

## Features

* **current weather and temperature**
* **forecast: hourly every 3 hours (next 12 hours, landscape mode for 15 hours) or daily for 4/5 days**
* **sunrise and sunset**
* **Moon phase**

### Plan to Add

* pizza index
* other things??

## Options

* **portrait and landscape mode**
* **landscape mode on Paperwhite!!** see configuration
* configurable place, units, language
* automatic night mode
* I am running this on a kindle papwerwhite 10th gen. The page displays great but the screen going to sleep is a challenge. Mobile Read forums usually has the most updated info on how to get around this. I was able to do it by jailbreaking the device and eventually creating a file that contains the command to disable the screensaver. The very short version of this is that as of at least early 2026, Amazon has removed the abilty to run commands via the search bar in the kindle paperwhite firmware. However, the commands still exist in the operating system and I was able to access them in this other way thanks to the lovely folks sharing what they have learned over on those forums. I'll post the exact thread if I can find it again.

Weather and forecast source: https://openweathermap.org/

Icons source: https://github.com/erikflowers/weather-icons

<img src="real_devices.jpg" width="300" alt="Dashboard on real devices" />

# How to run directly on the Kindle (tested on Kindle PW 3)
1. clone or download repository
2. generate your free API key (AppId) at http://openweathermap.org/appid
3. rename `config.js.sample` to `config.js` and set the parameters you need (all parameters are optional and can be set in the HTML webpage `config.html`, but I recommend setting at least the `api_appId`)
4. copy the folder with all files to the root of Kindle storage
5. disable the screensaver on your Kindle:
  * press the search button (or keyboard button on Kindle 4) on homescreen and type: `;debugOn` and press enter on the keyboard
  * press the search button (or keyboard button on Kindle 4) again and type: `~disableScreensaver` and press enter on the keyboard. (On Kindle Paperwhite, type: `~ds` - with new firmware this may not be possible, but see these [instructions](https://github.com/matopeto/kindle-weather-dashboard/issues/16) for a solution)
6. launch the browser on your Kindle and go to: `file:///mnt/us/kindle-weather-dashboard/index.html` (where `kindle-weather-dashboard` is the folder in the root of your Kindle storage from step 4)

## Configuration
### with config.js
create a config.js file from config.js.sample and set variables:

* `api_locParams` - query parameters to set location (e.g. `lat=50&lon=14`, or `q=Paris`)
* `api_appId` - set your `API KEY (appId)` from http://openweathermap.org/appid
* `api_lang` - output language (e.g. `en`, default: `en`)
* `api_units` - units: `metric` (°C), `imperial` (°F), `standard` (K) (default: `metric`)
* or you can set all API parameters at once with the `api_params` variable (e.g. `q=Prague&appid=YOUR_API_KEY&lang=sk&units=metric`). **Note:** when `api_params` is set, `api_locParams`, `api_appId`, `api_lang`, `api_units` and their URL counterparts (`city`, `lat`, `lon`, `appId`, `lang`, `units`) are ignored.
* `rotation` - force rotation (on Kindle Paperwhite) `ll` for left landscape, `lr` for right landscape, and `up` for upside down (default: none)
* `night_mode` - `auto` - based on sunrise and sunset, `on` - always on, `HH-HH` (`22-06`) interval for on/off, `off` or `null` to disable (default: `off`)
* `refreshTime` - refresh rate in milliseconds (default: 30 minutes)
* `utcOffset` - if not set, it is determined by location (default: `auto`), `local` - local machine UTC offset, or custom UTC offset. (Because Kindle doesn't report the correct local time. You may need to change the value after the winter/summer time change)
* `tempType` - use `feelsLike` for current weather and hourly forecast; daily forecast uses actual min/max temps (default: `actual`)
* `forecastType` - `hour` for 3-hour steps or `daily` for daily forecast (default: `hour`)

See more: http://openweathermap.org/current, http://openweathermap.org/forecast and http://openweathermap.org/forecast16

### with url query parameters
* `appId` sets the appId
* `city` sets the city (e.g. `city=Paris`)
* `lat`, `lon` set location (e.g. `lat=50&lon=14`)
* `lang` sets language (default: `en`)
* `units` sets units: `metric` (°C), `imperial` (°F), `standard` (K) (default: `metric`)
* `rotation` sets the rotation (default: none)
* `utcOffset` sets UTC offset (default: auto by location)
* `tempType` sets temperature type - `actual` or `feelsLike` (default: `actual`)
* `forecastType` sets forecast type - `hour` or `daily` (default: `hour`)
* `night` sets night mode - `off`, `auto`, `on` (default: `off`)
* `refreshTime` sets refresh interval in minutes (default: 30)

Examples:
* Dashboard for Prague, metric units, Slovak language: `http://YOUR_URL/?city=Prague&lang=sk&units=metric&appId=YOUR_API_KEY`
* Dashboard for a given GPS location, metric units, default language: `https://YOUR_URL/?lat=50&lon=14&units=metric&appId=YOUR_API_KEY`

## Screenshots

### Kindle 4
<img src="screenshot_kindle4.gif" width="300" alt="Kindle 4 screenshot" />

### Kindle Paperwhite 3
<img src="screenshot_paperwhite3.png" width="300" alt="Kindle Paperwhite 3 screenshot" />

### Real devices
<img src="real_devices.jpg" width="300" alt="Dashboard on real devices" />
