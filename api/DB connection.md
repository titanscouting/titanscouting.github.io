---
permalink: /api/db-connection
title: Connecting the API to MongoDB
---

# Overview 
To allow the API to retrieve data from MongoDB, the API must be informed as to the address of the database, as well as the username and password used to connect. Since these values are sensitive, they may not be committed to source control. As such, environment variables must be used. The production server is configured with the appropriate environment variables to connect to the database. This page will describe how to configure your local development machine to connect to the database.
*Note: while we currently use the same database for testing and production, this* **will** *change in the future. Be cognizant of this change when it comes to protect our data*

## Configuring WSL development

## Configuring Docker development
