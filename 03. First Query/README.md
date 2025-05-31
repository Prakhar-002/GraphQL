<h1  align="center" > 🏕️ 𝐅𝗂𝗋𝗌𝗍 𝐐υ𝖾𝗋𝗒 🏚️</h1>

</br>

<p  align="center" >

| Part           | Purpose                                   |
| -------------- | ----------------------------------------- |
| `typeDefs`     | Define **what data** can be queried       |
| `resolvers`    | Define **how to get the data**            |
| `ApolloServer` | Ties it all together                      |
| Sandbox        | Lets you test your GraphQL queries easily |

</p>

```js
// Import ApolloServer class from the Apollo Server package
import { ApolloServer } from "@apollo/server";

// Import the function to start a standalone Apollo server
import { startStandaloneServer } from "@apollo/server/standalone";

// Create a new ApolloServer instance with type definitions and resolvers
const server = new ApolloServer({
  // Define GraphQL schema using SDL syntax
  typeDefs: `#graphql
        type Query {
            hello: String        // Query field 'hello' returns a String
        }
    `,

  // Define resolver functions to provide data for schema fields
  resolvers: {
    Query: {
      // Resolver for 'hello' field returns a greeting string
      hello: () => "Hello world!",

      // 'ids' is incorrectly placed here; resolvers should be functions
      // This line does not have effect and should be removed or fixed
      ids: ["id_1", "id_2", "id_3"],
    },
  },
});

// Start the server on port 4000 and get the URL
const { url } = await startStandaloneServer(server, {
  listen: { port: 4000 },
});

// Log the server URL once ready
console.log(`🚀  Server ready at: ${url}`);

```

#### Inside the sandbox

```graphql
query Demo {
  hello
}
```
