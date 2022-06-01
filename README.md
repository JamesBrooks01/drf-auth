# LAB - Class 33

## Project: Authentication & Production Server

## Author: James Brooks

## Setup

- To run the app, if you have docker, use `docker compose up`
  - If not, run `python manage.py runserver` within a virtual environment

### CRUD Routes

- Tokens
  - To get an access and refresh token, send a POST request to `/api/token` with the username and password in the JSON body.
  - To refresh your access token, send a POST request to `/api/token/refresh` with the refresh token in the JSON body
- List View
  - For a GET request, send your access token as a bearer token to `/api/v1/snacks`
  - For a POST request, send the access token as a bearer token and the following in the JSON body.
    - purchaser
    - title
    - description
- Detail View
  - The detail view is at `/api/v1/snacks/<id>` and has GET, PUT, and DELETE requests
  - One thing of note is that you can only access the PUT and DELETE with the token that corresponds to the user that created it.
  - For the GET and PUT routes, they need the same information as the list route
  - The DELETE only requires the bearer token.

## Tests

- To run the tests, use the `python manage.py test` within a virtual environment
- There are 7 tests in total, with tests for testing the Snack model, the views and the CRUD routes, plus an additional test for requiring authentication to see the list page.
- Currently, the last test gives a 401 status code when unauthenticated, and the test is expecting a 403 code.
