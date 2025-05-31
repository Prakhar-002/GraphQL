<h1  align="center" > 🏕️ 𝐎ρ𝖾𝗋α𝗍𝗂ⱺ𐓣 𝐀𝗋𝗀υꭑ𝖾𐓣𝗍𝗌 🏚️</h1>

### inside the index.js file

```js
const server = new ApolloServer({
  // Define schema with Query type having two fields: greetings and add
  typeDefs: `#graphql
    type Query {
        greetings(name: String): String!   // greetings takes an optional name argument and returns a non-nullable String
        add(a: Int!, b: Int!): Int          // add takes two non-nullable Int arguments and returns an Int
    }
    `,

  // Resolver functions for Query type fields
  resolvers: {
    Query: {
      // greetings resolver examples commented out:
      // logs arguments and returns greeting message
      // greetings(parent, args, ctx, info) {
      //   console.log(args);
      //   return `Hello ${args.name}`;
      // },

      // greetings resolver using destructuring of arguments
      // greetings: (_, { name }) => `Hello ${name}`,

      // add resolver takes arguments a and b, returns their sum
      add: (_, { a, b }) => a + b,
    },
  },
});

```

### inside the sandbox

```graphql
{
  greetings(name: "Jordan")
  add(a: 10, b: 20)
}
```
