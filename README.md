# Weather API

Deploys a weather API proxy to tell you the temperature for a given US city.

## Local Deploy

As this API proxies requests to a third-party weather API, an API key from [openweathermap.org](openweathermap.org) is required. Place it in `./Worker/Dockerfile` line 16.

Deploy this on your local computer via Docker, after ensuring you have a relatively recent version:

```
~/weather-api $ docker-compose up
```

If all goes well, visit [http://localhost:8087/temp.php?city=Kona](http://localhost:8087/temp.php?city=Honolulu).

## Production Deploy

Deploy to your pre-existing AWS ECS cluster (cluster creation not covered here):

```
~/weather-api $ ecs-cli compose --project-name TemperatureAPI -f ecs-compose.yml service up
```

Again, if all goes well, you should have the API accessible at http://**YOUR-ECS-IP**/temp.php?city=Honolulu
