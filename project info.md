# IMT 542 G8
# Project: centralized surfing information platform

## About
This platform is designed for surfers looking to explore new destinations. Currently, there is no unified source that consolidates information about various surf spots. As a result, surfers often need to browse multiple websites to find details such as the best surf seasons, water temperatures, and nearby amenities.
Our platform solves this problem by aggregating essential data for each surf location such as ideal surf seasons, average water temperature, detailed location, and surrounding facilities. This centralized system allows surfers to efficiently plan their trips and make informed decisions before hitting the waves.

## Methodology
### Data quality
Sources: We collect data such as water temperature from official sources that use buoy-based measurements. Information about nearby amenities is aggregated from travel websites and platforms like Google Maps. For future development, we aim to include user-generated content such as comments, blogs, and travel posts to enrich our database. However, incorporating this type of content will require additional effort for verification and moderation.

Null Values: Missing values are filled with "Unknown" by default. If a destination has limited data, we allow users to contribute information. These contributions are clearly marked as community-sourced and pending verification, so other users can interpret them accordingly.

Quality Checks: Users can submit feedback on the accuracy of any information. If content appears outdated or incorrect, users can flag it through an error report feature. These reports help us maintain quality and identify gaps in the data. User feedback is an essential part of our quality assurance process.

### Deleting records
To prevent permanent loss of data and allow users to recover deleted entries, we use a soft-delete strategy. Instead of removing a record from the database, we set a `deleted: true` flag on the item.

## Access
The platform will be presented as the form of a map. When users' cursor hovers at a location, surfing spots of that location will appear on the map.
Click on the points of surfing spots, it will show the information of that spot (e.g., "name": "Uluwatu", "country": "Indonesia", "wave_type": "reef break", "difficulty": "advanced", "best_season": ["May", "Sep"], "swell": ["SW", "S"], "water_temp": "26–29°C", "amenities": ["rentals", "cafés"]).
If users wish to learn more about the location, they can click on the "details" to know more details.

## Structure
Field          Type        Description 
`name`        string   Surf spot name (e.g. "Uluwatu")
`country`     string   Country where the surf spot is located
`wave_type`   string   Type of wave: beach, reef, or point break
`difficulty`  string   Difficulty level: beginner, intermediate, advanced
`best_season` array    Best surf months (e.g. `["May", "Sep"]`)
`swell`       array    Ideal swell directions (e.g. `["SW", "S"]`)
`water_temp`  string   Typical water temperature range in °C
`hazards`     array    List of common dangers (e.g. `["reef", "currents"]`)
`amenities`   array    Nearby services (e.g. `["rentals", "cafés"]`)  

## Example
GET /spots?country=Indonesia&difficulty=advanced

Host: surfapi.example.com

