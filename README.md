# Node-GraphQL-Prisma-Example
A Node implementation of GraphQL with Prisma.

## Setup
```
npm install
npx prisma migrate save --experimental
npx prisma migrate up --experimental
npx prisma generate
```

## Run Server
```
node src/index.js
```

## Explore Data
```
npx prisma studio --experimental
```

## Queries/Mutations
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
