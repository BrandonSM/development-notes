# GraphQL (with React + Relay)

GraphQL describes how you want your data in the form of a "Graph". It was invented by Facebook in (<insert year>)

Some of the problemes it solves include:
- Multiple expensive API calls to get data you want
- Subscriptions to data sources

```Example
 Get user ID (but also includes name, age, etc.. ), Get all friends of user (also includes their names, ages, and friends...), Get the companies they work for (also includes the companies founded date, users, etc... )
 ```

With `GraphQL` you can describe your data like this and only get the names of the companies of a user's friends.

```Example
query(id: 23) {
  user {
    friends {
      companies {
        name
      }
    }
  }
}
```

## Schema

GraphQL Schemas can act like a relational database.

```
[--  USER --]        [-- POSTS --] 
id:                  id:
name:                title: 
login:               user:  USER.id 
```


## Query

The `Root Query` is the entry point into the graph. `query(User: 23) { }` means get "Get the details of the user with the id of 23"

```JavaScript
// If you'r elooking for a user, if you give me an ID, I'll give you a user
// in the resolve resolve function, this is where your logic goes
const RootQuery = new GraphQLObjectType({
  name: 'RootQueryType',
  fields: {
    user: {
      type: UserType,
      args: { id: { type: GraphQLString }},
      // this is where you actually go into the database and do something
      // the rest of the schema object just dsecribes how your data should look, 
      // the resolve() function actually does something
      // eg.... when you go into the database and look for a user (it's in the User field)


      resolve(parentValue, args) {
        // first `parentValue` argument is rarely used
      
        // second argument, with whatever arguments gets passed, 
        // use these... if it needs an id, it will be present on the args object
      }
    }
  }
})
```


```
{
  user(id: "23") {
    id,
    firstName,
    age
  }
}