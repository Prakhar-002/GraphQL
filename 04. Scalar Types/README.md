<h1  align="center" > 🏕️ 𝐒𝖼αᥣα𝗋 𝐓𝗒ρ𝖾𝗌 🏚️</h1>

</br>

### Inside the index.js file

```js
// Create a new ApolloServer instance demonstrating GraphQL scalar types
const server = new ApolloServer({
  // Define the GraphQL schema with scalar types for the Query type
  typeDefs: `#graphql
        type Query {
            id: ID!          // Unique identifier, non-nullable
            name: String     // String type
            age: Int         // Integer type
            isActive: Boolean// Boolean type
            height: Float    // Floating-point number type
        }
    `,
  // Provide resolver functions to return sample data for each field
  resolvers: {
    Query: {
      id: () => "1",            // Returns string "1" as ID
      name: () => "John Doe",   // Returns a sample name
      age: () => 30,            // Returns an integer
      isActive: () => true,     // Returns a boolean value
      height: () => 5.6,        // Returns a float value
    },
  },
});

```

### inside the sandbox

```graphql
{
  id
  name
  age
  isActive
  height
}
```
