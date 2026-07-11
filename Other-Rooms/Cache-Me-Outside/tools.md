# Cache Me Outside — Tools Reference

## Komoot
- **Purpose**: Outdoor activity / fitness profile platform
- **Usage**: Profile search by user ID reveals real name and linked accounts
- **Command**: Open `https://www.komoot.com/user/{user_id}`

## GitHub (API & .patch)
- **Purpose**: Code hosting platform with commit metadata
- **Usage**: Commit history exposes author email addresses
- **API Endpoint**: `https://api.github.com/repos/{owner}/{repo}/commits`
- **Patch URL**: `https://github.com/{owner}/{repo}/commit/{sha}.patch`

## Threads / Instagram
- **Purpose**: Social media platforms
- **Usage**: Username search reveals posts with location-specific content
- **URL**: `https://www.threads.com/@{username}`

## Google Lens
- **Purpose**: Image recognition and reverse image search
- **Usage**: Identify storefronts, signs, and landmarks from photos

## Google Maps
- **Purpose**: Mapping and transit route planning
- **Usage**: Find nearest tram/bus stops to a geolocated address

## Sherlock (optional)
- **Purpose**: Username enumeration across social networks
- **Usage**: `sherlock jiml33t` to discover associated platforms

## Email Client (Active OSINT)
- **Purpose**: Trigger automated email replies
- **Usage**: Send email to discovered address; auto-reply may contain phone number, address, or other PII
