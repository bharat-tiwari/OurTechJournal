# Introduction

## GraphQL

GraphQL is a query language that provides a new way of coding your API layer end points which is more flexible and efficient compared to REST.

With GraphQL:

* client can specify exactly what data it needs and in what format it needs the data
* you can specify your data model schemas with strongly typed data types using GraphQL's Schema Language
* its easy to aggregate data from multiple sources with just one call compared to multiple calls that may be needed with REST 
* returns JSON

### Comparing to REST

* Requires continuous upgrading of documentation
* Code Redundancy and increased complexity could easily get introduced if endpoints need to be configured to send different properties of same data

    e.g \* an endpoint for basic User Profile 

  * an endpoint for detailed user profile with email and profile pic

with REST, you client would receive a response like below:

```javascript
"user": {
    "id": "AA0001",
    "email" : "user1@test.com",
    "createdOn": "12324982132",
    "servicePlan": "Premium"
}
```

But what if client is only interested in `id` and `servicePlan`. With REST, your client has to filter the needed data on the client side or else server has to create another endpoint to return only those properties. With graphQL, client can specify exactly what data it needs in the query and will get response accordingly

```javascript
{
    "data": {
      "user": {
        "id": "AA0001",
        "servicePlan": "Premium"
      }
    }
}
```

## References

[http://graphql.org/blog/rest-api-graphql-wrapper/](http://graphql.org/blog/rest-api-graphql-wrapper/)

[https://dev-blog.apollodata.com/full-stack-react-graphql-tutorial-582ac8d24e3b](https://dev-blog.apollodata.com/full-stack-react-graphql-tutorial-582ac8d24e3b)

[https://www.howtographql.com/](https://www.howtographql.com/)

[http://graphql.org/learn/schema/](http://graphql.org/learn/schema/)

[http://dev.apollodata.com/react/](http://dev.apollodata.com/react/)

