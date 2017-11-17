
# Node API Skeleton

Combining the Node.js/ES6 libs du jour for the purpose of providing JSON APIs for apps.

* Babel/ES6 transpiling
* Express for middleware
* Jest for testing, Supertest for mocking express
* Persistence using Mongoose/MongoDB
* Dockerized using Alpine and Yarn
* User signup, login and password reset API using JSON Web Token
* JSON Rest API for user management (admin)
* User encryption using BCrypt
* AirBnB style syntax and ES linting
* Configuration using environment variables

_Note: A Python version of this project can be found [here](https://github.com/dominiek/python-api-skeleton)_

## Directory Structure

* `package.json` - Configure dependencies
* `config/defaults.json` - Default configuration, all values can be controlled via env vars
* `dist/*` - Files generated by babel
* `src` - All source code
* `src/*/__tests__` - Unit tests
* `src/run.js` - Entrypoint for running and binding API
* `src/lib` - Library files like utils etc
* `src/api` - Express routes
* `src/middleware` - Middleware libs
* `src/models` - Models for ORM (Mongoose)
* `src/index.js` - Entrypoint into API (does not bind, so can be used in unit tests)

## API Routes

All routes are name spaced with a v1 version:

```
POST    /1/users                       # Create user (signup)
POST    /1/users/sessions              # Create session / jwt (login)
GET     /1/users/self                  # Get my user info
DELETE  /1/users/self                  # Delete my account
POST    /1/users/self                  # Update my account
POST    /1/users/password/forgot       # Get forgot password token
POST    /1/users/password/reset        # Use reset password token to set new password
GET     /1/users                       # Admin: Search/List users
GET     /1/users/:user_id              # Admin: Get user
DELETE  /1/users/:user_id              # Admin: Delete user
POST    /1/users/:user_id              # Admin: Update user
```

## Install Dependencies

```
yarn install
```

## Testing & Linting

```
yarn test
yarn lint
```

## Running in Development

Code reload using nodemon:

```
yarn dev
```

## Configuration

All values in `config/defaults.json` can be overwritten using environment variables. For example `bind.host` becomes can be overwritten using the `API_BIND_HOST` environment variable.

- `API_BIND_HOST` - Host to bind to, defaults to `"0.0.0.0"`
- `API_BIND_PORT` - Port to bind to, defaults to `3005`
- `API_MONGO_URI` - MongoDB URI to connect to, defaults to `mongodb://localhost/skeleton_dev`

## Building the Container

```
docker build -t node-api-skeleton .
```

## Todo

- [x] Basic ES6 express example
- [x] Jest unit testing example of mocked express
- [x] Add Mongoose persistence example
- [x] Add await/async test case
- [x] Make Mongoose test code await/async
- [x] Add Mongoose + Express + await/async test case
- [x] Add admin user management API
- [x] Add signup and session API
- [x] Document API
- [x] Document directory structure
- [x] Add AirBnB base
- [x] Fix up all ES linting errors
- [x] Use promises for init portion
- [x] Add environment var based config
- [x] Add user attribute cleansing
- [x] Fix docker
- [x] Add forgot password API
