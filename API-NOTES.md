# API Notes

| API | Endpoint used | Key needed | Something we learned |
| --- | --- | --- | --- |
| Open-Meteo | `https://api.open-meteo.com/v1/forecast?latitude=..&longitude=..&current=temperature_2m,relative_humidity_2m,wind_speed_10m,weather_code&daily=weather_code,temperature_2m_max,temperature_2m_min,precipitation_probability_max&timezone=Asia%2FColombo&forecast_days=3` | No | The `daily` data comes back as parallel arrays: index 0 of every array is day 1. Weather is described by numeric WMO codes that we translate in `describeWeather()`. |
| Frankfurter | `https://api.frankfurter.dev/v2/rate/usd/lkr` | No | The response is one small object and the number we need is `rate`. We cache it in `usdToLkrRate`, so it is requested only once per page load. |
| Leaflet + OpenStreetMap | `https://tile.openstreetmap.org/{z}/{x}/{y}.png` (tiles) and `leaflet@1.9.4` from unpkg | No | A map is many small tile images arranged by Leaflet. The OpenStreetMap credit (attribution) is required by their usage policy, and the map container needs a fixed height. |
