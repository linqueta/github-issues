# Github Issues

## The test

This test has the goal to make a complete api for receive, save and get some data about github issues. You must do these tasks bellow:

### Tasks
1. [Repository](#1-repository)
2. [Github Webhook](#2-github-webhook)
3. [Models](#3-models)
4.

### 1. Repository

- Fork this repository with your account and do the tests using your forked repository
- After you end the test, you must notify who contact you

### 2. Github Webhook

- You must integrate your api to receive data about your repository's issues by Github Webhook integration. You may see more about it [here](https://developer.github.com/webhooks)
- For you receive data in localhost you could use [ngrok](https://ngrok.com/) as a vpn.

### 3. Models
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

### 4. The api
- You must develop a REST api with some routes, they are:
  - GET /repositories

    The route must return all repositories data sorted ascending by the Github created at. Follow an example bellow:

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

    The route must return all data about the repository. If the repository doesn't exist must be returned a http_code 404. Follow an example bellow:

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



