<h1  align="center" > 🏕️ 𝐀𝗋𝗋α𝗒𝗌 ω𝗂𝗍ɦ 𝐒𝖼αᥣα𝗋 𝐓𝗒ρ𝖾𝗌 🏚️</h1>

</br>

### inside the index.js file

```js
const typeDefs = `#graphql
  type Query {
    greetings: [String]      // Returns a list of greeting strings
    luckyNumbers: [Int]      // Returns a list of integers representing lucky numbers
    temperatures: [Float]    // Returns a list of floating-point numbers (temperatures)
    flags: [Boolean]         // Returns a list of boolean values
    ids: [ID]                // Returns a list of IDs (unique identifiers)
  }
`;

const resolvers = {
  Query: {
    greetings: () => ["Hello", "Hi", "Hey"],             // Resolver returns an array of greeting strings
    luckyNumbers: () => [3, 7, 13],                       // Resolver returns an array of integers
    temperatures: () => [22.5, 23.8, 21.9],               // Resolver returns an array of floats
    flags: () => [true, false, true],                     // Resolver returns an array of booleans
    ids: () => ["abc123", "def456", "ghi789"],            // Resolver returns an array of string IDs
  },
};

```

### Inside the sandbox

```graphql
query {
  greetings
  luckyNumbers
  temperatures
  flags
  ids
}
```
