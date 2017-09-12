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
  type UserDetails {
    id: String
    name: String
    email: String
  }
  
  // Query(GET) endpoints typedefs go inside the parent type `Query`
  type Query {
     UserDetails: UserDetails
  }
  
  // Mutations(PUT/POST) endpoints typedefs go inside the parent type `Mutation`
  type Mutation {
   UserEmail(id: String!, email: String!): Channel
  }
`];


 
```

## Resolvers

```js
const resolvers = {
  Query: {
    UserDetails ({ id }, context) {
       return request('GET')
         .from(await route(`user/${id}`))
         .send<{ UserDetails }>()
         .then((res) => res.data.user)
         .catch((err) => {
            // throw error
       });
    }
  },
  Mutation: {
    UserEmail: (args) => {
    
      { id, email } = args;
      const res = request('PUT')
                 .from(`user/${id}`)
                 .withData({email})
                 .send();
      return {
        ...res.data.email,
        id: id
      };
   }
  },
};
```


## Make Executable Schema
Once you have typeDefs and Resolvers set up, you make a executable schema that GraphQL can execute using the `graphql-tools's` `makeExecutableSchema` function:

```js

// schema.ts

import typeDefs from './schema';
import resolvers from './resolvers';

const schema = makeExecutableSchema({ typeDefs, resolvers });
```

## Set up Express to use graphQLExpress middleware
Once we have our executable schema ready, we can provide it to graphQLExpress to set it as a middleware for our node Express server:

```js
server.use('/graphql', bodyParser.json(), graphqlExpress({
  schema
}));

//also set up the endpoint for the `GraphiQL` query editor tool:
server.use('/graphiql', graphiqlExpress({
  endpointURL: '/graphql'
}));
```

This is server side setup for GraphQL in brief. Next we'll set the client side setup needed for GraphQL

 
 
 


 



