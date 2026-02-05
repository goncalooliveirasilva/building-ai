<!-- This is the markdown template for the final project of the Building AI course,
created by Reaktor Innovations and University of Helsinki.
Copy the template, paste it to your GitHub README and edit! -->

# Wardrobe AI

Final project for the Building AI course.

## Summary

An AI assistant that predicts the optimal outfit type based on weather conditions (temperature, wind speed, rain) and planned activity (walking, office, sports). Instead of guessing from a thermometer reading, it learns from past data that 15ºC with wind feels very different from 15°C in calm sunshine.

## Background

Choosing what to wear seems trivial, but most people get it wrong regularly:

- **Temperature alone is misleading**: 15°C in spring sunshine feels warm, but 15°C with autumn wind and drizzle feels cold. A simple thermometer check doesn't capture this.
- **Activity matters**: the right outfit for a morning jog is very different from one for sitting in an office, even in the same weather.
- **Daily friction**: everyone faces this decision every morning. Getting it wrong means being during the day.

My personal motivation is that I check the weather app every morning and still end up making bad choices sometimes, especially during transitional seasons.

## How is it used?

The user provides (or the system fetches from a weather API) the current conditions:

1. Temperature (°C)
2. Wind speed (m/s)
3. Is it raining (yes/no)
4. Planned activity (walking, office, sports, casual)

The model returns a clothing recommendation such as: _t-shirt_, _light jacket_, _sweater_, _heavy coat_, _rain jacket_, or _sportswear layers_.

A typical scenario: you wake up, check the app, enter that it's 12°C, windy, no rain, and you're walking to work. The model tells you to grab a windbreaker instead of the heavy coat you might instinctively reach for.

The primary users are everyday people who want a quick, practical recommendation.

**You can check my example implementation in [this notebook](./initial-version.ipynb).**

## Data sources and AI methods

The training data would be collected by hand initially: logging daily weather, activity, and what clothing felt right.  
Over time this could be expanded with weather data from open APIs like [OpenWeatherMap](https://openweathermap.org/api) for real-time conditions.

**AI method: k-Nearest Neighbors (k-NN)**

k-NN is a good fit. It handles the non-linear interactions naturally (e.g., wind + low temperature = much colder feel) without needing to manually engineer a formula. It also outputs categorical labels directly, which matches the clothing categories.

## Challenges

- **Small dataset**: with hand-collected data, the training set will be small at first, which limits k-NN accuracy. The model improves as more data is logged.
- **Missing context**: the model doesn't account for humidity, sun exposure, duration of outdoor time.

## What next?

- Connect to a live weather API so the user only needs to specify their activity
- Build a simple interface
- Add user feedback to continuously improve predictions
- Incorporate more features: humidity, UV index, time outdoors

## Acknowledgments

- [Building AI course](https://buildingai.elementsofai.com/)
- [OpenWeatherMap](https://openweathermap.org/)
- [scikit-learn documentation](https://scikit-learn.org/)
