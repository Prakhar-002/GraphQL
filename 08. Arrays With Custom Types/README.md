<h1  align="center" > 🏕️ 𝐀𝗋𝗋α𝗒𝗌 𝐖𝗂𝗍ɦ 𝐂υ𝗌𝗍ⱺꭑ 𝐓𝗒ρ𝖾𝗌 🏚️</h1>

</br>

### inside the index.js file

```js
const typeDefs = `#graphql
  // Movie type definition with id, title, and release year
  type Movie {
    id: ID               // Unique identifier
    title: String        // Movie title
    releaseYear: Int     // Year the movie was released
  }

  // Post type definition with id, title, body content, and published status
  type Post {
    id: ID               // Unique identifier
    title: String        // Post title
    body: String         // Content of the post
    published: Boolean   // Publication status of the post
  }

  // User type definition with id, name, email, and age
  type User {
    id: ID               // Unique identifier
    name: String         // User's full name
    email: String        // User's email address
    age: Int             // User's age
  }

  // Root Query type to fetch lists of movies, posts, and users
  type Query {
    movies: [Movie]      // Returns an array of Movie objects
    posts: [Post]        // Returns an array of Post objects
    users: [User]        // Returns an array of User objects
  }
`;

const resolvers = {
  Query: {
    // Resolver for movies returns a list of movie objects
    movies: () => [
      { id: "1", title: "Inception", releaseYear: 2010 },
      { id: "2", title: "Interstellar", releaseYear: 2014 },
      { id: "3", title: "The Dark Knight", releaseYear: 2008 },
    ],

    // Resolver for posts returns a list of post objects
    posts: () => [
      { id: "1", title: "Post 1", body: "Body of post 1", published: true },
      { id: "2", title: "Post 2", body: "Body of post 2", published: true },
      { id: "3", title: "Post 3", body: "Body of post 3", published: false },
    ],

    // Resolver for users returns a list of user objects
    users: () => [
      { id: "1", name: "John Doe", email: "jZ6Wv@example.com", age: 30 },
      { id: "2", name: "Jane Doe", email: "jZ6Wv@example.com", age: 25 },
      { id: "3", name: "Bob Smith", email: "jZ6Wv@example.com", age: 40 },
    ],
  },
};

```

```graphql
{
  movies {
    id
    title
    releaseYear
  }

  posts {
    id
    title
    body
    published
  }

  users {
    id
    name
    age
    email
  }
}
```
