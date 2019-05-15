# Github Issues

## The test

This test has the goal to make a complete API for receive, save and get some data about Github issues. You must do these tasks below:

### Tasks
1. [Instructions](#1-instructions)
2. [Repository](#2-repository)
3. [Github Webhook](#3-github-webhook)
4. [Models](#4-models)
5. [The api](#5-the-API)
6. [Tests](#6-tests)
7. [Extras](#7-extras)

### 1. Instructions
- The test must be developed with Ruby on Rails and you may choose your best test suite. After you did all tasks, you must write instructions at least to run the API and to run the tests in another file with the name INSTRUCTIONS.md.

### 2. Repository

- Fork this repository with your account and do the tests using your forked repository
- After you end the test, you must notify who contact you

### 3. Github Webhook

- You must integrate your API to receive data about your repository's issues by Github Webhook integration. You may see more about it [here](https://developer.github.com/webhooks)
- For you receive data in localhost you could use [ngrok](https://ngrok.com/) as a VPN

### 4. Models
- You must develop three models with their respective fields, they are:
  - Repository:
    - external_id (Github repository id)
    - name
    - clone_url
    - owner (Github repository owner login)
    - external_created_at
    - external_updated_at
  - Issue
    - external_id (Github issue id)
    - url
    - title
    - external_created_at
    - external_updated_at
  - IssueAction
    - action
    - sender (Github sender login)

### 5. The API
- You must develop a REST API with some routes, they are:
  - GET /repositories

    The route must return all repositories data sorted ascending by the Github created at. Follow the example below:

    Request:
    ```
    GET /repositories
    ```
    Response:
    ```javascript
    [
      {
        "id": 135493233,
        "name": "Hello-World",
        "clone_url": "https://github.com/Codertocat/Hello-World.git",
        "owner": "Codertocat",
        "created_at": "2018-05-30T20:18:04Z",
        "updated_at": "2018-05-30T20:18:10Z"
      }
    ]
    ```
    * The fields id, created_at and updated_at are from Github

  - GET /repositories/:repository_id

    The route must return all data about the repository. If the repository doesn't exist must be returned a http_code 404. Follow the example below:

    Request:
    ```
    GET /repositories/135493233
    ```
    Response:
    ```javascript
    {
      "id": 135493233,
      "name": "Hello-World",
      "clone_url": "https://github.com/Codertocat/Hello-World.git",
      "owner": "Codertocat",
      "created_at": "2018-05-30T20:18:04Z",
      "updated_at": "2018-05-30T20:18:10Z",
      "issues": [
        {
          "id": 327883527,
          "url": "https://api.github.com/repos/Codertocat/Hello-World/issues/2",
          "title": "Spelling error in the README file",
          "created_at": "2018-05-30T20:18:32Z",
          "updated_at": "2018-05-30T20:18:32Z",
          "actions": [
            {
              "action": "opened",
              "sender": "Codertocat"
            },
            {
              "action": "edited",
              "sender": "Codertocat"
            },
            {
              "action": "deleted",
              "sender": "Codertocat"
            }
          ]
        }
      ]
    }
    ```
    * The fields id, created_at, updated_at and repository_id are from Github
    * The node "issues" must be sorted by its create date
    * The node "actions" must be sorted by its notification date

### 6. Tests
- You must develop some tests for check controllers, webhook entrance and other things. You may choose how you will code it and what tests are necessary to ensure that all is working.

### 7. Extras
- All listed here isn't required in this test, but, these extras tasks may add points in your score. The extras tasks are:
  - UI to list repositories and permit to find a repository and show its details
  - GraphQL API to get and mutate repository and issues data
  - Develop some CI to check automatically your tests