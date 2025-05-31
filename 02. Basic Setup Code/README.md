<h1  align="center" > 🏕️ 𝐁α𝗌𝗂𝖼 𝐒𝖾𝗍υρ 𝐂ⱺᑯ𝖾 🏚️</h1>

1. Create index.js file and paste the following code:

```js
// Import ApolloServer class from the @apollo/server package
import { ApolloServer } from "@apollo/server";

// Import the function to start the server in standalone mode
import { startStandaloneServer } from "@apollo/server/standalone";

// Create a new ApolloServer instance with type definitions and resolvers
const server = new ApolloServer({
   typeDefs,    // GraphQL schema definitions (must be defined elsewhere)
   resolvers,   // Resolvers to handle the queries (must be defined elsewhere)
});

// Start the server on port 4000
const { url } = await startStandaloneServer(server, {
   listen: { port: 4000 }, // Server will listen on port 4000
});

// Log the URL where the server is running
console.log(`🚀  Server ready at: ${url}`);

```
