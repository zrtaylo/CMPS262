# CMPS262
Point Park University Advanced Programming

## Synopsis

This project allows users to get the current weather through the web browser by using the native Geo-location feature. As I continue development, I hope to include functionality to get the forecast in whichever city the user searches for.

## Code Example

**This code allows the application to display the corresponding information for the weather icon, temperature, a basic description, and the city and country the user is searching from.**
```
function displayWeather(){
    iconElement.innerHTML = `<img src="icons/${weather.iconId}.png"/>`;
    tempElement.innerHTML = `${weather.temperature.value}°<span>C</span>`;
    descElement.innerHTML = weather.description;
    locationElement.innerHTML = `${weather.city}, ${weather.country}`;
}
```
**The API returns the temperature in KELVIN. The "temperature" function converts the temperature to Celsius, while this function converts the temperature to Fahrenheit.**
```
function celsiusToFahrenheit(temperature){
    return (temperature * 9/5) + 32;
}
```
**This code sets up an EventListener that calls the temperature conversion function when the user clicks the displayed temperature.**

```
tempElement.addEventListener("click", function(){
    if(weather.temperature.value === undefined) return;

    if(weather.temperature.unit == "celsius"){
        let fahrenheit = celsiusToFahrenheit(weather.temperature.value);
        fahrenheit = Math.floor(fahrenheit);

        tempElement.innerHTML = `${fahrenheit}°<span>F</span>`;
        weather.temperature.unit = "fahrenheit";
    }else{
        tempElement.innerHTML = `${weather.temperature.value}°<span>C</span>`;
        weather.temperature.unit = "celsius"
    }
});
```
## API Reference

This project uses the OpenWeather API at https://openweathermap.org/api.


## Contributors

Zachary Taylor
