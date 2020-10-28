---
permalink: /api/annotated-example
title: Annotated Route and Database Handler example
---

# Overview
This file contains an annotated example of a route and a database handler from the source code.
## Example Route - Annotated (src/routes/fetch2022Schedule.ts)

    import UserReturnData from '../UserReturnData'; // import the data struct which stores data to return to the user
    import StatusCodes from '../StatusCodes'; // import standard HTTP code responses

    module.exports = (app: any, dbHandler: any) => {
    app.get('/api/fetch2022Schedule', async (req: any, res:any) => { // route name, accessible at /api/fetch2022schedule
        const val: UserReturnData = new UserReturnData(); // initialize variable which will contain the data to return to the user
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
