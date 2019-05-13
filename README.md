# Github Issues

## The test

This test has the goal to make a complete api for receive, save and get some data about github issues. You must do these tasks bellow:

### Tasks
1. [Repository](#1-repository)

### 1. Repository

- Fork this repository with your account and do the tests using your forked repository
- After you end the test, you must notify who contact you

### 2. Github Webhook

- You must integrate your api to receive data about your repository's issues by Github Webhook integration. You may see more about it [here](https://developer.github.com/webhooks)
- For you receive data in localhost you could use [ngrok](https://ngrok.com/) as a vpn.

### 4. Models
- You must develop three models with their respective fields, they are:
  - Repository:
    - external_id
    - name
    - clone_url
    - external_created_at
    - external_updated_at
  - Issue
    - external_id
    - url
    - title
    - external_created_at
    - external_updated_at
  - IssueAction
    - action
    -

### 3. The api
- You must develop some apis, they are:
  - GET /repositories/:repository_id
    The route must return informations about repository


