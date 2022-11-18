---
permalink: /api/annotated-example
title: Annotated Route example
---

# Overview
This document contains an annotated example of a route and a database handler from the source code.
This document can be used as somewhat of a checklist as to what files must be created and changed when writing a new endpoint.

## Example Route (src/routes/fetchTeamSchedule.ts)
~~~javascript
import { validate, Joi } from 'express-validation'; // query parameters validation tool
import UserReturnData from '../UserReturnData'; // datastruct to model the JSON that is sent to the user
import StatusCodes from '../StatusCodes'; // simple interface for all the status codes that the API can return, and what they mean
import Scouter from '../Scouter'; // datastruct to model a human scouter and their attributes

module.exports = (app: any, dbHandler: any, auth: any) => {
  const validation = {
    query: Joi.object({
      competition: Joi.string().required(),
    }),
  } // define the validation schema - in this case, the user is required to provide the competition ID as a query parameter
  app.get('/api/fetchTeamSchedule', auth.checkAuth, validate(validation, { keyByField: true }, { allowUnknown: true }), async (req: any, res:any) => {
    // auth.checkAuth checks user credentials (Google or API key)
    // `validate()` runs validation using the defined schema, and allows keys that aren't present in the validation schema (such as CLIENT_ID and CLIENT_SECRET)
    const val: UserReturnData = new UserReturnData();
    const competition = String(req.query.competition);
    const scouter: Scouter = { name: String(res.locals.name), id: String(res.locals.id), team: String(res.locals.team) }; 
    // force conversion to string - may not be needed anymore but was added to all routes as a quick-fix during competition.
    
    val.data = await dbHandler.fetchTeamSchedule(req.db, competition, scouter).catch((e) => { console.error(e); val.err_occur = true; }); 
    
    // grab data from the database using the associated DB handler - if there is an error, throw an error and mark an error to the user.
    // Notice how we pass the scouter to the DB handler - this allows the DB handler to get the user's team, which we have verified with their credentials.
    
    if (val.err_occur === false) { // if our request successfully retrieves data from the DB, return it to the user
      res.json({
        success: true,
        competition,
        team: scouter.team,
        data: val.data.data,
      });
    } else { // otherwise, mark the assocciated HTTP status code in the response and tell the user an error occured.
      res.status(StatusCodes.no_data).json({
        success: false,
        reasons: val.err_reasons,
      });
    }
  });
};
~~~
## Example Database Handler (src/db-handlers/fetchTeamSchedule.ts)
~~~javascript
import Scouter from '../Scouter';
import UserReturnData from '../UserReturnData';

export default async (db: any, competition: string, scouter: Scouter): Promise<UserReturnData> => {
  const data: UserReturnData = { err_occur: false, err_reasons: [], data: {} };
  const dbo = db.db('data_scouting'); // go to the scouting data DB
  const myobj = { teams: { $all: [scouter.team] }, competition, owner: scouter.team }; // query the database using Mongo query language - get all matches where the team is the scouter's team and in the given competition. Only return matches that are in this team's instance of TRA.
  try {
    data.data = await dbo.collection('matches').find(myobj).toArray(); // run the query and output to array
  } catch (err) {
    data.err_occur = true; // notify frontend an error occured
    data.err_reasons.push(err.toString());
    console.error(err);
  }
  return data;
}
~~~

## Example entry in src/index.ts 
~~~javascript

require('./routes/base')(app); // line 34
// bunch of routes skipped here for length
require('./routes/fetchTeamSchedule')(app, dbHandler, auth); 
// ^ an instance of the express app, as well as the dbHandler object and the auth checker is provided to the route.
require('./routes/checkUserTeam')(app, auth);

// start the server and export for use in the unit tests, etc. 
~~~

## Example entry in src/dbHandler.ts
~~~javascript
export { default as addKey } from './db-handlers/addKey'; //line 3
// bunch of handlers skipped here for length
export { default as fetchTeamSchedule } from './db-handlers/fetchTeamSchedule';
~~~

## Example Unit Test entry in test/fetchTeamSchedule.js

Note: this unit test entry is a bit flawed because it only checks for the simplest case. Unit tests should also verify that the API behaves as expected when not provided authentication credentials, when bad data is given, required paramters aren't given, etc. Ideally, it should also verify a few traits of the data (such that there are X number of matches with each match having 6 teams).

~~~javascript
process.env.NODE_ENV = 'test';

const chai = require('chai');
const chaiHttp = require('chai-http');

const server = require('../src/index.ts');

const should = chai.should();

chai.use(chaiHttp);
// all above is boilerplate: allows us to use the testing framework to make assertions, 
// and gets an instance of the API server to start

/*
  * Test the GETroute
  */
describe('GET /api/fetchTeamSchedule', () => { // describe what endpoint we're testing
  it('it should GET the schedule for 2022', (done) => { // describe the expected behavior for this test
    chai.request(server)
      .get(`/api/fetchTeamSchedule?competition=2020ilch&CLIENT_ID=${process.env.TRA_CLIENTID}&CLIENT_SECRET=${process.env.TRA_CLIENTSECRET}`) // make the request, providing the API with the client ID and secret for authentication. This must be present as an environment variable on the machien running the tests (such as GitHub runners, etc.)
      .end((err, res) => {
        res.should.have.status(200); // expect the status to be 200 OK
        res.body.should.have.property('data'); // check JSON property
        res.body.should.have.property('success').eql(true); // should be successful.
        done();
      });
  });
});
~~~

