---
permalink: /api/db-connection
title: Connecting the API to MongoDB
---

# Overview 
To allow the API to retrieve data from MongoDB, the API must be informed as to the address of the database, as well as the username and password used to connect. Since these values are sensitive, they may not be committed to source control. As such, environment variables must be used. The production server is configured with the appropriate environment variables to connect to the database. This page will describe how to configure your local development machine to connect to the database.  
*Note: while we currently use the same database for testing and production, this* **will** *change in the future. Be cognizant of this change when it comes to protect our data*

## Configuring WSL development
  1. Obtain the MongoDB connection URI from the Titan Scouting lead.
  2. Open a command prompt in WSL (either from the Start Menu or from VS Code will do). 
  3. Type `nano ~/.bashrc` to edit your user's .bashrc file. This file is executed when you first log into WSL. 
  4. Navigate to the end of the file using your arrow keys.
  5. Paste the following line at the end of the file, replacing `{MONGO_URI}` with the URI provided to you as such:  
    ```export REDALLIANCEDBKEY="{MONGO_URI}"```
  6. Press Ctrl-x, y, and then enter to save your changes and exit
  7. In the terminal prompt run `source ~/.bashrc` to apply the changes. 

The next time you start the API, the key will be provided to the application and it will be able to connect to the MongoDB instance.

## Configuring Docker development
The Docker development environment is configured through VS code. We will edit a file to provide the docker container with the correct environment variable. 
  1. Open VS Code and open the API source code folder.  <ins>***DO NOT reopen the folder in container if prompted.*** </ins>
  2. Expand the .devcontainer folder
  3. Create a file named `.env`
  4. In this file, type this, replacing `{MONGO_URI}` with the URI provided to you as such:  
    ```REDALLIANCEDBKEY="{MONGO_URI}"```
  5. Click the green remote connections button on the bottom left of the screen, and click `Remote Container: Reopen in Container`, and wait for the container to build and open your development environment.
