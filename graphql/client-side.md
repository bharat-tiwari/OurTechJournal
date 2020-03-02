# Client Side

## Client side setup \(Apollo GraphQL client\)

Apollo GraphQL client manages the data store \(cache\) and network requests from our client application to the GraphQL server.

### Create NetworkInterface and ApolloClient

For our front-end React application to communicate to GraphQL server, we first setup the network interface. Then we set up the ApolloClient providing it the this graphQL's network interface.

```javascript
// imports....
import { ApolloClient, createNetworkInterface } from 'apollo-client';

const networkInterface = createNetworkInterface({
  uri: '/graphql'
});

export const client = new ApolloClient({ networkInterface });
```

### Setting up React components to work with GraphQL

For our React components to work with Apollo GraphQL Client, we need to wrap the react component inside a Higher-order Component called `graphQL` provided by `react-apollo` library. This High-order component would pass down the response from GraphQL server's query or mutation to the wrapped react component.

For a component that is calling a **query**, the response will be sent as `data` object:

`{ data: { ...responseData, loading: true/false, error: {} }`

Note the `loading` property available in the data object to indicate if the data query is in progress or over.

For a component that is calling a **mutation**, the graphQL will pass down a `mutate` object that we can use to call the mutation on GraphQL server

`{ mutate: { variables from mutation response } }`

#### React component using a query

#### React component using a mutation

```javascript
import React from 'react';
import { gql, graphql } from 'react-apollo';

// Component function
class UpdateUserEmailReactComponent extends React.Component {
  { mutate } = this.props;

  const updateUserEmail = (evt) => {
    if (evt.keyCode === 13) {
      mutate({ 
        variables: { 
             { 
                userEmail: { evt.target.value } 
             } 
        }
      })
      .then( res => {
        // email updated successfully
      });
    }
  };
  return (
    <input
      type="text"
      placeholder="Enter Email"
    />
    <button type="button" onclick="updateUserEmail">Update Email</button>
  );
};


const updateUserEmailMutationQuery = gql`
  mutation mutateUserEmail($userId: String!, $email: String!) {
    UserEmail(id: $userId, email: $email) {
      id
      email
    } 
  }
`;

type UserEmail {
  email: string 
  id: string
}

const UpdateUserEmailGraphQLComponent = graphql(
  updateUserEmailMutationQuery
)(UpdateUserEmailReactComponent);


export default UpdateUserEmailGraphQLComponent;
```

## Options to update Client after Mutation

To update the client state after a mutation, we have three options: 1. Use mutate objects 'Refetch' property to specify the queries to rerun that could be affected by the mutation 2. Use mutate objects 'Update' method to update the client state based on the mutation result 3. Use GraphQL subscriptions to notify clients about updates.

### Refetch

```javascript
  // updateUserEmail.ts
  ...
  import { userDetails } from './user/UserDetails';

  ...
  // make email mutate
  mutate(
     variables: { 
                userEmail: { evt.target.value } 
     },
     refetchQueries: [ {query: userDetails} ]  //this would refetch the userDetails 
  )
```

### Store Update

In the above approach, the mutation actually costed the client two trips to server. The first one for mutation and then second one for the refetching the affected data. This approach may not get us best user experience for clients with low network latency.

For such scenarios, the `graphQL` component's mutation object exposes us an `Update` function that gets called when the mutation completes. The update function provides us the `store` \(cached data store of Apollo Client\) object. We can use to this `Update` function to construct a payment type transaction object and push it the transactionsList available in `store`.

```javascript
    // updateUserEmail.ts
    ...

    ...
    // make email mutate
    mutate(
      variables: { 
         userEmail: { evt.target.value } 
      },
      update: (store, { data }) => {
        { email } = data;

        const userDetails = store.readQuery({ query: userDetailsQuery });

        userDetails.email = email;
        store.writeQuery({ query: userDetailsQuery, userDetails });
     }
  )
```

### GraphQL Subscriptions

This is useful when multiple clients need to be updated when some data gets mutated.

## Optimistic UI

[https://dev-blog.apollodata.com/tutorial-graphql-mutations-optimistic-ui-and-store-updates-f7b6b66bf0e2](https://dev-blog.apollodata.com/tutorial-graphql-mutations-optimistic-ui-and-store-updates-f7b6b66bf0e2)

