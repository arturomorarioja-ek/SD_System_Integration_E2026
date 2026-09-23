### Tasks
Create a GraphQL API in the programming language of your choice that serves the following data store:

```
[
  {'title': 'Learn GraphQL', 'completed': False},
  {'title': 'Build a GraphQL API', 'completed': True},
  {'title': 'Test the API', 'completed': False},
  {'title': 'Keep learning', 'completed': False},
]
```

**Endpoint**: `/tasks`

**Queries**

All tasks
```graphql
{
  "query": "{ tasks { title completed } }"
}
```

One task by title
```graphql
{
  "query": "query($t:String!){ task(title:$t){ title completed } }",
  "variables": { "t": "Learn GraphQL" }
}
```

**Mutations**

Add a task
```graphql
{
  "query": "mutation{ addTask(title:\"Buy groceries\"){ success task{ title completed} } }"
}
```

Update a task
```graphql
{
  "query": "mutation{ updateTask(title:\"Buy groceries\", newTitle:\"Buy groceries and snacks\", completed:true){ success task{ title completed} } }"
}
```

Delete a task
```graphql
{
  "query": "mutation{ deleteTask(title:\"Test the API\"){ success deletedTask{ title completed } } }"
}
```
