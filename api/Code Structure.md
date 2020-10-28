---
permalink: /api/code-structure
title: General Code Structure
---

# Overview
This document contains a brief overview of how the API code is structured to help you more efficiently navigate the repository. The `src` folder contains the main source code for the routes and database handlers that provide information to the user and get information from the database. The `test` folder contains unit tests for the API code, as applicable. The `public` folder contains any files to be provided raw to the public, such as the privacy policy. The `deploy` folder contains deployment files to deploy to Docker Compose and k8s.

To view an annotated route and database handler, click [here](/api/annotated-example).
## Main API code 
The main `src` folder contains data return structures and the main modules for our code.

### src
* `index.ts` is the main API file, which imports all of the routes from `src/routes`, provides them with the required parameters, and then runs the API server.
* `dbHandler.ts` is the main database handler file, which imports and reexports the database handler files to consolidate them into a module.  
  * Database handlers are files corresponding to each route which allows the route to query the database for the appropriate information. For example, the route `fetch2022Schedule.ts` in `src/routes` also has a database handler named `fetch2022Schedule.ts` in `src/db-handlers`.
* `Scouter.ts` is a data structure which represents a scouter. It contains the name, Google ID, and team number of a user.
* `UserReturnData.ts` is a data structure for data returns to the REST API. It contains the data, whether an error occured, and if an error occured the reason that the error occured. 
* `StatusCodes.ts` is a data structure which contains the [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) which are provided to the user depending on various return scenarios. These codes cover:  
    * 200: Success
    * 404: No data or not enough information
    * 401: Not authorized 
        * 403: API key authentication not allowed
* `authHandler.ts` verifies the identity of users that are accessing authenticated routes. This handler verifies both Google and API key-based access attempts. To learn more about the authentication system for the API, click [here](/api/authentication)

### src/routes
Each TypeScript file contains the code for a specific route, which is executed when a user queries the API. This file contains code for parameter verification and data returns to the user.

### src/db-handlers
Each TypeScript file contains the code which fetches the data from the database for the route with the corresponding name. See above for an explanation of the system. This file contains code for querying the database, as well as any manipulation which needs to be done to the retrieved data.

## Deployment files (deploy)