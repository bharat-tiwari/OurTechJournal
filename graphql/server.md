# Server side setup for GraphQL

GraphQL's server side setup has following important components:

1. **typeDefs** - Type definitions aka **schema** of your data models and shapes/contract defs of your queries and mutations. (Think of **Queries** and **Mutations** as your GraphQL server's endpoints. Queries are for GET, Mutations can be for PUT or POST.)

2. **resolvers** - functions/code for your queries and mutations. These function signature should match with the signature that you have defined in your queries/mutations schema. In these functions, you write code for how or where to get or post data, and then resolve/customize/massage the response data as defined in the typeDefs of data models. ( for example a resolve function could contain a MongoDB/Mongoose find statement to query some data or even could be an Axios call to query some external REST API endpoint)

## TypeDefs / Schema

type definitions of data models, queries and mutations:
 - are written in [GraphQL Schema Language](http://graphql.org/learn/schema/). 
 - are first written in a templated string format (within a pair of backticks (\`...`)
 
```js
 const typeDefs = [`
  type AccountBalance {
    currentBalance: String
    pastDue: String
    amountDue: String
    unbilledCharges: String
    currency: String
  }
`];

export default Balance;
 
```

## Resolves

## Make Executable Schema
 
 
 


 



