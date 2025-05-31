<h1  align="center" > 🏕️ 𝐂υ𝗌𝗍ⱺꭑ 𝐓𝗒ρ𝖾𝗌 🏚️</h1>

</br>

### Inside the index.js file

```js
const server = new ApolloServer({
  // Define schema with Post type and Query type
  typeDefs: `#graphql
    type Post {
        id: ID!           // Unique non-nullable ID for each post
        title: String!    // Non-nullable title of the post
        body: String!     // Non-nullable body content of the post
        tags: [String]    // Optional list of tags associated with the post
    }

    type Query {
        posts: [Post]     // Query returns a list of Post objects
    }
    `,
  // Resolver functions for the Query type
  resolvers: {
    Query: {
      // Resolver for 'posts' returns an array of post objects
      posts: () => [
        {
          id: "1",
          title: "Post 1",
          body: "Body of post 1",
          tags: ["tag1", "tag2"],  // Tags for post 1
        },
        {
          id: "2",
          title: "Post 2",
          body: "Body of post 2",
          tags: ["tag3", "tag4"],  // Tags for post 2
        },
      ],
    },
  },
});

```

### Inside the sandbox

```graphql
{
  posts {
    id
    title
    body
    tags
  }
}
```
