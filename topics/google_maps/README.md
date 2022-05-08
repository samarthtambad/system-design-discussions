
# Google Maps

## Functional Requirements
1. Searching for places
2. Path between two locations
3. Given a location, search for certain kinds of places nearby
4. Add/update places
5. Reviews/ratings for places

## Non-Functional Requirements
1. High availability
2. availability > consistency
3. Low latency

## Scale Estimation
queries per second = 100k 
monthly users = 150M
new places added per day = 
read heavy

## Database Design

locations table
id,title,desc,lat,long,type,address

1 billion locations * 1kB = 1TB
increase yoy = 10%

over a period of 10 years = 10TB

- SQL vs no-SQL
- What data structure could be used for efficient searching?
- 
- 






