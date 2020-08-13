# Node-GraphQL-Prisma-Example
A Node implementation of GraphQL with Prisma.

## Setup
```
npm install
npm run migrate
```

## Run Server
```
npm run serve
```

## Explore Data
```
npm run explore
```

## Mutations
**Sign Up**
```
mutation {
  signup(
    name: "Admin"
    email: "admin@admin.com"
    password: "password"
  ) {
    token
    user {
      id
    }
  }
}
```

**Log In**
```
mutation {
  login(
    email: "admin@admin.com"
    password: "password"
  ) {
    token
    user {
      id
      name
      email
      links {
        id
        url
        description
      }
    }
  }
}
```

**HTTP Headers**
```
{
  "Authorization": "Bearer <Token>"
}
```

**Post**
```
mutation {
  post(
    url: "davidengel.dev"
    description: "An awesome portfolio site!"
  ) {
    id
  }
}
```

**Vote**
```
mutation {
  vote(linkId: 1) {
    link {
      url
      description
    }
    user {
      id
      name
      email
    }
  }
}
```

## Queries
**Feed**
```
query {
  feed(
    filter: "david"
    take: 1
    skip: 0
    orderBy: {
      createdAt: asc
    }
  ) {
    count
    links {
      id
      url
      description
      postedBy {
        id
        name
        email
      }
      votes {
        user {
          id
          name
          email
        }
      }
    }
  }
}
```

## Subscriptions
**New Links**
```
subscription {
  newLink {
      id
      url
      description
      postedBy {
        id
        name
        email
      }
  }
}
```

**New Votes**
```
subscription {
  newVote {
    id
    link {
      id
      url
      description
    }
    user {
      id
      name
      email
    }
  }
}
```
