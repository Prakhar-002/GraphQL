<h1  align="center" > 🏕️ 𝐑𝖾ᥣα𝗍𝗂ⱺ𐓣 𝐁α𝗌𝗂𝖼𝗌 🏚️</h1>

### inside the index.js

```js
const typeDefs = `#graphql
  // User type with non-nullable id and name, and a list of non-nullable posts
  type User {
    id: ID!               // Unique identifier (non-nullable)
    name: String!         // User's name (non-nullable)
    posts: [Post!]!       // List of posts by the user (non-nullable list of non-nullable Post objects)
  }
 
  // Post type with non-nullable id, title, optional content, and a non-nullable author
  type Post {
    id: ID!               // Unique identifier (non-nullable)
    title: String!        // Post title (non-nullable)
    content: String       // Post content (optional)
    author: User!         // The author of the post (non-nullable User object)
  }

  // Root Query to fetch all users and posts, both non-nullable lists with non-nullable elements
  type Query {
    users: [User!]!       // Returns list of users
    posts: [Post!]!       // Returns list of posts
  }
`;

const users = [
  { id: "1", name: "Alice" },   // Sample user Alice
  { id: "2", name: "Bob" },     // Sample user Bob
];

const posts = [
  {
    id: "101",
    title: "GraphQL Basics",
    content: "Intro to GraphQL",
    authorId: "1",              // Reference to author Alice by ID
  },
  {
    id: "102",
    title: "Advanced GraphQL",
    content: "Deep dive",
    authorId: "1",              // Reference to author Alice by ID
  },
  {
    id: "103",
    title: "Node.js Tips",
    content: "Some tips",
    authorId: "2",              // Reference to author Bob by ID
  },
];

const resolvers = {
  Query: {
    users: () => users,          // Resolver returns all users
    posts: () => posts,          // Resolver returns all posts
  },
  User: {
    // Resolver for user's posts: filters posts where authorId matches user's id
    posts: (parent) => posts.filter((post) => post.authorId === parent.id),
  },
  Post: {
    // Resolver for post's author: finds the user with matching id to post's authorId
    author: (parent) => users.find((user) => user.id === parent.authorId),
  },
};

```

### Inside the sandbox

```graphql
# Example 1

query {
  users {
    name
    posts {
      title
    }
  }
}
```

```graphql
# Example 2

query {
  posts {
    title
    author {
      name
    }
  }
}
```
