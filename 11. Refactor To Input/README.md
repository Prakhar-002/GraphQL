<h1  align="center" > 🏕️ 𝐑𝖾𝖿α𝖼𝗍ⱺ𝗋 𝐓ⱺ 𝚰𐓣ρυ𝗍 🏚️</h1>

#### Inside the index.js file

```js
const typeDefs = `#graphql
  // User type defines the structure of a user object
  type User {
    id: ID!               // Unique identifier, non-nullable
    first_name: String!   // User's first name, non-nullable
    last_name: String!    // User's last name, non-nullable
    email: String!        // User's email, non-nullable
    password: String!     // User's password, non-nullable
  }

  // Query type to fetch data
  type Query {
    users: [User!]!       // Returns a non-nullable list of User objects
  }

  // Input type for adding a user, encapsulates user fields
  input AddUserInput {
    first_name: String!   // Required first name field
    last_name: String!    // Required last name field
    email: String!        // Required email field
    password: String!     // Required password field
  }

  // Mutation type for creating or modifying data
  type Mutation {
    addUser(input: AddUserInput!): User!  // Mutation to add a user, expects AddUserInput, returns created User
  }
`;

let users = [];        // In-memory array to store users
let idCounter = 1;     // Auto-incrementing ID counter

const resolvers = {
  Query: {
    users: () => users,  // Resolver to return all users
  },

  Mutation: {
    // Resolver to add a new user from input object
    addUser: (_, { input }) => {
      const { first_name, last_name, email, password } = input;

      // Check if a user with the same email already exists
      if (users.find((user) => user.email === email)) {
        throw new Error("User already exists");
      }

      // Create new user object with auto-generated ID
      const newUser = {
        id: idCounter++,
        first_name,
        last_name,
        email,
        password,
      };

      users.push(newUser);  // Add new user to in-memory storage
      return newUser;       // Return the newly created user
    },
  },
};

```

### Inside the sandbox

```graphql
mutation {
  addUser(
    input: {
      first_name: "James"
      last_name: "ford"
      email: "james@example.com"
      password: "secure123"
    }
  ) {
    id
    first_name
    last_name
    email
  }
}
```
