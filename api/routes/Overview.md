---
permalink: /api/routes/list
title: Routes List
---

# Routes List

The following is a brief overview of all of the routes in the TRA API.

| Route | Protocol(s)  | Brief Overview |
| ------| ------------ | -------------- |
| /     | GET          | Base to verify API is running |
| /api/addAPIKey | POST | Allows the creation of API keys from current OAuth users |
| /api/addScouterToMatch | POST | Adds an authenticated user as scouting a given team for a given match |
| /api/addUserToTeam | POST | Adds a user to an FRC Team in the database |
| /api/checkUser | GET | Check to see if a User or API Key is valid |
| /api/fetch2022Schedule | GET | Get the match schedule for FRC Team 2022 at a given competition |
| /api/fetchAllTeamNicknamesAtCompetition | GET | Get all the team nicknames at a given competition |
| /api/fetchCompetitionSchedule | GET | Get all the matches for a given competition and what users are scouting the match |
| /api/fetchMatchConfig | GET | Get the match scouting page configuration |
| /api/fetchMatchData | GET | Get the scouted data for a given match at a given competition |
| /api/fetchMatches | GET | Get the list of matches and the number of scouters for the match |
| /api/fetchPitConfig | GET | Get the pit scouting page configuration |
| /api/fetchMatchData | GET | Get the scouted pit data for a given team at a given competition |
