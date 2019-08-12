# GraphQL (with React + Relay)

GraphQL describes how you want your data. It solves one problem of a bunch of expensive API calls.

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

