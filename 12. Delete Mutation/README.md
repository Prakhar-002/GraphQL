<h1  align="center" > 🏕️ 𝐃𝖾ᥣ𝖾𝗍𝖾 𝐌υ𝗍α𝗍𝗂ⱺ𐓣 🏚️</h1>

### Inside the index.js file

```js
const typeDefs = `#graphql
  // User type defines user fields
  type User {
    id: ID!              // Unique identifier, non-nullable
    first_name: String!  // User's first name, non-nullable
    last_name: String!   // User's last name, non-nullable
    email: String!       // User's email, non-nullable
    password: String!    // User's password, non-nullable
  }

  // Query type to fetch users
  type Query {
    users: [User!]!      // Returns a list of users, non-nullable
  }

  // Input type for adding a new user
  input AddUserInput {
    first_name: String!  // Required first name
    last_name: String!   // Required last name
    email: String!       // Required email
    password: String!    // Required password
  }

  // Mutation type for adding and deleting users
  type Mutation {
    addUser(input: AddUserInput!): User!   // Adds a new user and returns it
    deleteUser(id: ID!): User!             // Deletes user by ID and returns deleted user
  }
`;

let users = [];       // In-memory users array
let idCounter = 1;    // Auto-increment ID

const resolvers = {
  Query: {
    users: () => users,   // Returns all users
  },
  Mutation: {
    // Add user mutation resolver
    addUser: (_, { input }) => {
      const { first_name, last_name, email, password } = input;

      // Check if user with email exists
      if (users.find((user) => user.email === email)) {
        throw new Error("User already exists");
      }

      // Create new user object with unique ID
      const newUser = {
        id: idCounter++,
        first_name,
        last_name,
        email,
        password,
      };

      users.push(newUser);   // Add new user to array
      return newUser;        // Return created user
    },

    // Delete user mutation resolver
    deleteUser: (_, { id }) => {
      // Find user index by matching ID (casting to string for safe comparison)
      const userIndex = users.findIndex(
        (user) => String(user.id) === String(id)
      );

      // Throw error if user not found
      if (userIndex === -1) {
        throw new Error("User not found");
      }

      const deletedUser = users[userIndex]; // Store deleted user data
      users.splice(userIndex, 1);            // Remove user from array
      return deletedUser;                    // Return deleted user
    },
  },
};

```

```graphql
mutation {
  deleteUser(id: "1") {
    id
    first_name
    email
  }
}
```
