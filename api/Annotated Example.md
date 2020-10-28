---
permalink: /api/annotated-example
title: Annotated Route and Database Handler example
---

# Overview
This document contains an annotated example of a route and a database handler from the source code.
This document can be used as somewhat of a checklist as to what files must be created and changed when writing a new endpoint.

## Example Route - Annotated (src/routes/fetch2022Schedule.ts)
~~~javascript
import UserReturnData from '../UserReturnData'; // import the data struct which stores data to return to the user
import StatusCodes from '../StatusCodes'; // import standard HTTP code responses

module.exports = (app: any, dbHandler: any) => { // accept the parameters provided in index.ts. If this was an authenticated route, auth would also be accepted
// auth.checkAuth would be used as Express middleware.
// See https://expressjs.com/en/guide/using-middleware.html for a guide to middleware. 
app.get('/api/fetch2022Schedule', async (req: any, res:any) => { // route name, accessible at /api/fetch2022schedule
    const val: UserReturnData = new UserReturnData(); // initialize variable which will contain the data to return to the user
    // UserReturnData is a data type and structure which we imported earlier to standardize API returns
    const competition = String(req.query.competition); // get competition ID
    if (!(competition)) { // indicate error if the competition was not provided. 
        val.err_occur = true;
        val.err_reasons.push('A required parameter (competition) was not provided'); 
    } else { // Only run the DB query if the correct info was provided
        val.data = await dbHandler.fetch2022Schedule(req.db, competition).catch((e) => { console.error(e); val.err_occur = true; }); // asynchronusly get data from the DB and store it in the UserReturnData instance. 
    }
    if (val.err_occur === false) { // if no error occured, return the data
    res.json({
        success: true,
        competition,
        data: val.data.data,
    });
    } else { // if an error occured, return that one occured and what error occured.
    res.status(StatusCodes.no_data).json({
        success: false,
        reasons: val.err_reasons,
    });
    }
});
};
~~~
## Example Database Handler - Annotated (src/db-handlers/fetch2022Schedule.ts)
~~~javascript
import UserReturnData from '../UserReturnData'; // import the data struct which stores data to return to the user

export default async (db: any, competition: string): Promise<UserReturnData> => { // take input of a DB instance and the competition
  const data: UserReturnData = { err_occur: false, err_reasons: [], data: {} }; // init the UserReturnData for storing values from the DB in
  const dbo = db.db('data_scouting'); // specify the databse to query
  const myobj = { teams: { $all: ['2022'] }, competition }; 
  // ^ specify the query to make. In this case, we are looking for all enteries where the team is 2022, and the competition is the specified competition
  try {
    data.data = await dbo.collection('matches').find(myobj).toArray(); // get the data from the DB and convert it from a cursor to an array
  } catch (err) {
    data.err_occur = true; // if an error occured, indicate that one occured and push the cause
    data.err_reasons.push(err);
    console.error(err); // log any errors to the console for debugging
  }
  return data;
}
~~~

## Example entry in src/index.ts
~~~javascript

require('./routes/base')(app); // line 34
// bunch of routes skipped here for length
require('./routes/fetch2022Schedule')(app, dbHandler); // an instance of the express app, as well as the dbHandler object is provided to the route.
require('./routes/checkUserTeam')(app, auth);

// start the server and export for use in the unit tests, etc. 
~~~

## Example entry in src/dbHandler.ts
~~~javascript
export { default as addKey } from './db-handlers/addKey'; //line 3
// bunch of handlers skipped here for length
export { default as fetch2022Schedule } from './db-handlers/fetch2022Schedule';
~~~

## Example Unit Test entry in test/fetch2022Schedule.js
~~~javascript
process.env.NODE_ENV = 'test';

const chai = require('chai');
const chaiHttp = require('chai-http');

const server = require('../src/index.ts');

const should = chai.should();

chai.use(chaiHttp);
// all above is boilerplate: allows us to use the testing framework to make assertions, and gets an instance of the API server to start

/*
  * Test the GET route
  */
describe('GET /api/fetch2022Schedule', () => { // describe the route that is being tested
  it('it should GET the schedule for 2022', (done) => { // describe the expected behavior
    chai.request(server)
      .get('/api/fetch2022Schedule?competition=2020ilch') // perform the request with the neccessary parameters
      .end((err, res) => {
        res.should.have.status(200); // check that the HTTP status is returned as 200 (signals success)
        res.body.should.have.property('data'); // check that there is a property called success
        res.body.should.have.property('success').eql(true); // check that the property success exists and is equal to `true`
        done(); //signal that this test is done 
      });
  });
});
~~~

