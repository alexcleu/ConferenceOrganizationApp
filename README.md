App Engine application for the Udacity training course. --Updated API for Udacity coursework

## Products
- [App Engine][1]

## Language
- [Python][2]

## APIs
- [Google Cloud Endpoints][3]

## Setup Instructions
1. Update the value of `application` in `app.yaml` to the app ID you
   have registered in the App Engine admin console and would like to use to host
   your instance of this sample.
1. Update the values at the top of `settings.py` to
   reflect the respective client IDs you have registered in the
   [Developer Console][4].
1. Update the value of CLIENT_ID in `static/js/app.js` to the Web client ID
1. (Optional) Mark the configuration files as unchanged as follows:
   `$ git update-index --assume-unchanged app.yaml settings.py static/js/app.js`
1. Run the app with the devserver using `dev_appserver.py DIR`, and ensure it's running by visiting your local server's address (by default [localhost:8080][5].)
1. (Optional) Generate your client library(ies) with [the endpoints tool][6].
1. Deploy your application.

##Setup prior to testing the API
1. Please make sure to create the conference first.
1. Please go down the tested endpoints method one by one


## Responses
1. Task 1: Explain in a couple of paragraphs your design choices for session and speaker implementation.
I have added conferencekey as a field in session, thus the session can be called on when a conferencekey is given. The conference keys are then first used to pull out all of the Sessions under the conference, and typeOfSession/Speakers were then checked for the queries.

1. Task 3: Write out two additional queries, and talk about the functionality
Two additional queries are used for scenario where the user needs to look for a particular session at the particular date. The first one was checked by the speaker and the tyepOfSession, and the second one was by the festival name and date. 

1. Let’s say that you don't like workshops and you don't like sessions after 7 pm. How would you handle a query for all non-workshop sessions before 7 pm? What is the problem for implementing this query? What ways to solve it did you think of?

answers: Two inequality filters are applied to the non-workstop. That is 
against the rule regarding to the query restrction, as all non-workshop 
session and the date time by 7 PM are two inequalities. To solve it, one can 
set up a query to look for all workshop sections (==), and then applies the 
inequality for >= 7 PM. 



[1]: https://developers.google.com/appengine
[2]: http://python.org
[3]: https://developers.google.com/appengine/docs/python/endpoints/
[4]: https://console.developers.google.com/
[5]: https://localhost:8080/
[6]: https://developers.google.com/appengine/docs/python/endpoints/endpoints_tool
