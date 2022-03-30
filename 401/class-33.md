# Reading Notes 33 -- Serverless & Amplify 

**Duplicate notes from yesterday because it was review content and the GraphQL I took notes on yesterday as well**

## Serverless

From [Hackernoon - Intro to Serverless](https://hackernoon.com/what-is-serverless-architecture-what-are-its-pros-and-cons-cc4b804022e9)

The Serverless model of web applications that removes much of the control and responsibility that comes with a traditional server setup. The serverless model is one of task executions, not a constant always running model like a traditional server. Serverless allows the application creator to combine third-party services, client-side logic, and functions as a service.

For many apps the serverless model will work well, but not everything. Traditional servers are still needed when access to the server IP is needed, when complex and long running functions are required, or when a large number of third party dependencies are needed. In general they are need when more control is desirable for security and in general and when the cost needs to be know ahead of time.

For many apps serverless will be more desirable because of the typically lower costs, scalability, speed of delivery, no back-end responsibility, 


## Amplify

From[AWS Amplify](https://aws.amazon.com/amplify/)

AWS Amplify is set of tools that simplifies working with many of the other AWS products. Amplify helps quickly setup the most common types of use cases for other AWS services. Amplify is meant to speed up app creation from frontend UI to backend data and connecting to outside services.

## GraphQL

From[Aplify Docs](https://docs.amplify.aws/cli-legacy/graphql-transformer/overview/)

GraphQL Transform uses the GraphQL Schema Definition Language to define your data models and transform it into a cloudformation template. With Amplify the command `amplify push` will deploy the cloudformation templates.

Directives 

  - `@model` defines object models for Amazon DynamoDB.
  - `@key` identifies the key for a model.
  - `@auth` used with Cognito for security.
  - `@conncetion` used for defining relationships between @models.
  - `@function` used to define a AWS Lambda resolver.
  - `@http` used to configure HTTP resolvers for CRUD operations to an endpoint.
  - `@predictions` used with Amazon services: Rekognition, Translate, and Polly.
  - `@searchable` used with Amazon Opensearch.
  - `@versioned` adds object versioning and conflict resolution to a type.

Task App Example

```java
    type Task
    @model
    @auth(rules: [
        {allow: groups, groups: ["Managers"], mutations: [create, update, delete], queries: null},
        {allow: groups, groups: ["Employees"], mutations: null, queries: [get, list]}
    ]) {
id: ID!
      title: String!
      description: String
      status: String
    }
type PrivateNote
@model
@auth(rules: [{allow: owner}]) {
id: ID!
      content: String!
}


# Create a task. Only allowed if a manager.
mutation CreateTask {
  createTask(input:{
title:"A task",
description:"A task description",
status: "pending"
}) {
    id
      title
      description
  }
}

# Get a task. Allowed if an employee.
query GetTask($taskId:ID!) {
  getTask(id:$taskId) {
    id
      title
      description
  }
}

# Automatically inject the username as owner attribute.
mutation CreatePrivateNote {
  createPrivateNote(input:{content:"A private note of user 1"}) {
    id
      content
  }
}

# Unauthorized error if not owner.
query GetPrivateNote($privateNoteId:ID!) {
  getPrivateNote(id:$privateNoteId) {
    id
      content
  }
}

# Return only my own private notes.
query ListPrivateNote {
  listPrivateNote {
    items {
      id
        content
    }
  }
}
```


