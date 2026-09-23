## Movie Streaming

**Part I**

Write a GraphQL SDL for a movie streaming platform with the following requirements:

Models:
- Movie (id, title, genre, duration in minutes, rating, is available, details, cast)
- Movie details (release year, language, age rating -e.g., "PG-13")
- Person (id, name, role)
- User (id, username, email, has subscription, favourite movies)

Enums
- Genre (ACTION, COMEDY, DRAMA, HORROR, SCIFI, OTHER)

Queries
- Movie by ID
- Movies by genre and average rating
- Users

Mutations
- Add movie (parameters: title, genre, duration in minutes)

**Part II**

Write the following queries:

1. Get the titles of all movies

2. Get a movie by ID

3. Get all action movies with an average rating of 4.0

4. Get all users with their favourite movies

5. Write a mutation to add the film *Inception* (science-fiction, 148 minutes).
