```
Ok(())
}
...
```

In this code, the API key is included in the request URL as a query parameter. The response is then parsed to retrieve and display the temperature in the specified city.

# Handling Errors and Rate Limits

When working with APIs, it's essential to handle errors gracefully. This includes managing rate limits, which restrict the number of API requests you can make within a certain timeframe. Let's add error handling and a basic rate limit management strategy to our weather fetching example:

```
/// use reqwest::blocking::Client; use serde::Deserialize; use std::error::Error; use std::thread; use std::time::Duration;

#[derive(Deserialize)]
struct Weather {
    main: Main,
    name: String,
}

#[derive(Deserialize)]
struct Main {
    temp: f64,
}

fn fetch_weather(api_key: &str, city: &str) -> Result<Weather, Box<dyn Error>> {
    let client = Client::new();
    let url = format!("https://api.openweathermap.org/data/2.5/weather?q={}&appid={}", city, api_key);
    let response = client.get(&url).send()?;
    if response.status().is_success() {
        let weather = response.json::<Weather>()?;
        Ok(weather)
```