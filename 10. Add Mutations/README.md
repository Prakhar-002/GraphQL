<h1  align="center" > 🏕️ 𝐀ᑯᑯ 𝐌υ𝗍α𝗍𝗂ⱺ𐓣𝗌 🏚️</h1>

### Inside the index.js file

```js
const typeDefs = `#graphql
  // User type with required fields
  type User {
    id: ID!               // Unique identifier (non-nullable)
    first_name: String!   // User's first name (non-nullable)
    last_name: String!    // User's last name (non-nullable)
    email: String!        // User's email (non-nullable)
    password: String!     // User's password (non-nullable)
  }

  // Query type to fetch list of users
  type Query {
    users: [User!]!       // Returns a non-nullable list of users
  }

  // Mutation type to add a new user
  type Mutation {
    addUser(
      first_name: String!, 
      last_name: String!, 
      email: String!, 
      password: String!
    ): User!              // Returns the newly added user (non-nullable)
  }
`;

let users = [];            // In-memory array to store users
let idCounter = 1;         // Simple counter to assign incremental IDs

const resolvers = {
  Query: {
    users: () => users,    // Resolver to return all users
  },
  Mutation: {
    // Resolver to add a new user
    addUser: (_, { first_name, last_name, email, password }) => {
      // Check if user with the same email already exists
      if (users.find((user) => user.email === email)) {
        throw new Error("User already exist");   // Throw error if duplicate
      }

      // Create new user object with incremented ID and provided data
      const newUser = {
        id: idCounter++, 
        first_name,
        last_name,
        email,
        password,
      };

      users.push(newUser);  // Add new user to the array
      return newUser;       // Return the newly created user
    },
  },
};

```

### Inside the sandbox

```graphql
mutation {
  addUser(
    first_name: "John"
    last_name: "Doe"
    email: "john@example.com"
    password: "secure123"
  ) {
    id
    first_name
    last_name
    email
  }
}
```
