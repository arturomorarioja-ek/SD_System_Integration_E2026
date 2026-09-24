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

### Solution

```graphql
schema {
    query: Query
    mutation: Mutation
}

type Query {
    movie(id: ID!): Movie
    movies(genre: Genre, minRating: Float): [Movie!]!
    users: [User!]!
}

type Mutation {
    addMovie(
        title: String!
        genre: Genre!
        durationMinutes: Int!
    ): Movie!
}

enum Genre {
    ACTION
    COMEDY
    DRAMA
    HORROR
    SCIFI
    OTHER
}

type Movie {
    id: ID!
    title: String!
    genre: Genre!
    durationMinutes: Int!
    rating: Float
    isAvailable: Boolean!
    details: MovieDetails!
    cast: [Person!]!
}

type MovieDetails {
    releaseYear: Int!
    language: String!
    ageRating: String!   # e.g. "PG-13"
}

type Person {
    id: ID!
    name: String!
    role: String!
}

type User {
    id: ID!
    username: String!
    email: String!
    hasSubscription: Boolean!
    favoriteMovies: [Movie!]!
}
```


**Part II**

Write the following queries:

1. Get the titles of all movies

  ```graphql
  query ListMovieTitles {
    movies {
      title
    }
  }
  ```

2. Get a movie by ID

  ```graphql
  query GetMovie {
    movie(id: "m1") {
      id
      title
      genre
      durationMinutes
      isAvailable
      details {
        releaseYear
        language
        ageRating
      }
      cast {
        name
        role
      }
    }
  }
  ```

3. Get all action movies with an average rating of 4.0

  ```graphql
  query MoviesByGenreAndRating {
    movies(genre: ACTION, minRating: 4.0) {
      title
      rating
      genre
    }
  }
  ```

4. Get all users with their favourite movies

  ```graphql
  query GetUsers {
    users {
      id
      username
      hasSubscription
      favoriteMovies {
        title
        genre
      }
    }
  }
  ```

5. Write a mutation to add the film *Inception* (science-fiction, 148 minutes).

```graphql
mutation {
  addMovie(
    title: "Inception"
    genre: SCIFI
    durationMinutes: 148
  ) {
    id
    title
    genre
  }
}
```
