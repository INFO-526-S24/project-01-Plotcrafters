# Data

We sourced the datasets for this project from tidytuesday's [github page](https://github.com/rfordatascience/tidytuesday/blob/master/data/2023/2023-06-20/readme.md).

-   **day_parts_map.csv**: Dates of certain astronomical events such as sunrise, solar noon, sunset, etc.

-   **places.csv**: Provides geographic coordinates and other location descriptors for where UFO sightings have taken place.

-   **ufo_sightings.csv**: Provides time and day, location, and anecdotal descriptors of the sighting including duration and craft shape at the sighting.

-   **ufo_sightings_with_time_of_day.csv**: Same as ufo_sightings.csv but with the additional column variable "time_of_day" which can take on a character data type of "morning", "afternoon", "evening", or "night".

# Codebook for day_parts_map.csv

| Variable Name               | Data type | Description                                                                                                                                                                                  |
|:----------------------------|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| rounded_lat                 | double    | Latitudes rounded to the tens digit.                                                                                                                                                         |
| rounded_long                | double    | Longitudes rounded to the tens digit.                                                                                                                                                        |
| rounded_date                | double    | Dates rounded to the nearest week.                                                                                                                                                           |
| astronomical_twilight_begin | double    | The UTC time of day when astronomical twilight began on this date in this location. Astronomical twilight begins when the sun is 18 degrees below the horizon before sunrise.                |
| nautical_twilight_begin     | double    | The UTC time of day when nautical twilight began on this date (or the next date) in this location. Nautical twilight begins when the sun is 12 degrees below the horizon before sunrise.     |
| civil_twilight_begin        | double    | The UTC time of day when civil twilight began on this date (or the next date) in this location. Civil twilight begins when the sun is 6 degrees below the horizon before sunrise.            |
| sunrise                     | double    | The UTC time of day when the sun rose on this date (or the next date) in this location.                                                                                                      |
| solar_noon                  | double    | The UTC time of day when the sun was at its zenith on this date (or the next date) in this location.                                                                                         |
| sunset                      | double    | The UTC time of day when the sun set on this date (or the next date) in this location.                                                                                                       |
| civil_twilight_end          | double    | The UTC time of day when civil twilight ended on this date (or the next date) in this location. Civil twilight ends when the sun is 6 degrees below the horizon after sunset.                |
| nautical_twilight_end       | double    | The UTC time of day when nautical twilight ended on this date (or the next date) in this location. Nautical twilight ends when the sun is 12 degrees below the horizon after sunset.         |
| astronomical_twilight_end   | double    | The UTC time of day when astronomical twilight ended on this date (or the next date) in this location. Astronomical twilight ends when the sun is 18 degrees below the horizon after sunset. |

# Codebook for places.csv

| Variable Name        | Data type | Description                                               |
|:---------------------|:----------|:----------------------------------------------------------|
| city                 | character | Unique cities in which sightings took place.              |
| alternate_city_names | character | Comma-separated other names for the city.                 |
| state                | character | The state, province, or similar division of the sighting. |
| country              | character | The name of the country.                                  |
| country_code         | character | The 2-letter country code of the sighting.                |
| latitude             | double    | The latitude for this city, from geonames.org.            |
| longitude            | double    | The longitude for this city, from geonames.org.           |
| timezone             | character | The timezone for this city, from geonames.org.            |
| population           | double    | The population for this city, from geonames.org.          |
| elevation_m          | double    | The elevation in meters for this city, from geonames.org. |

# Codebook for ufo_sightings.csv

| Variable Name          | Data type | Description                                                                                                                                                                                                                                                                                                                        |
|:-----------------------|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| reported_date_time     | datetime  | The time and date of the sighting, as it appears in the original NUFORC data.                                                                                                                                                                                                                                                      |
| reported_date_time_utc | datetime  | The time and date of the sighting, normalized to UTC.                                                                                                                                                                                                                                                                              |
| posted_date            | datetime  | The date when the sighting was posted to NUFORC.                                                                                                                                                                                                                                                                                   |
| city                   | character | The city of the sighting. Some of these have been cleaned from the original data.                                                                                                                                                                                                                                                  |
| state                  | character | The state, province, or similar division of the sighting.                                                                                                                                                                                                                                                                          |
| country_code           | character | The 2-letter country code of the sighting, normalized from the original data.                                                                                                                                                                                                                                                      |
| shape                  | character | The reported shape of the craft.                                                                                                                                                                                                                                                                                                   |
| reported_duration      | character | The reported duration of the event, in the reporter's words.                                                                                                                                                                                                                                                                       |
| duration_seconds       | double    | The duration normalized to seconds using regex.                                                                                                                                                                                                                                                                                    |
| summary                | character | The reported summary of the event.                                                                                                                                                                                                                                                                                                 |
| has_images             | logical   | Whether the sighting has images available on NUFORC.                                                                                                                                                                                                                                                                               |
| day_part               | character | The approximate part of the day in which the sighting took place, based on the reported date and time, the place, and data from sunrise-sunset.org. Latitude and longitude were rounded to the 10s digit, and the date was rounded to the week, to match against time points such as "nautical twilight", "sunrise", and "sunset." |
