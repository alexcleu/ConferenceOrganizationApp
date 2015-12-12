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

Sesson model:
I made the starttime in time property, date in dateproperty, and duration in float property. This helps the query more accurate as we build more api that supports the object type in the future. The data is stored in datastore, and it shown to the clients through protocol buffer. Everything in protocol buffer is in input in strings, but it will be translated to appropriate types in the datastore. 

The Session key is generated by the addition of the conference key. Although the session key will be long, but it will capture not only the conference it is associated it to, it can be used to locate the Profile that had created the Conference. 

Speaker implementation:
I decided speaker in the Session model. While creating a new session, the speaker can be added in the session. Featured speaker can be checked by the cache as the session gets createdd. The API will look under the datastore to look for potential sessions that also have the same speaker. If it does, it will display the result in cache. 


1. Task 3: Write out two additional queries, and talk about the functionality
Two additional queries( MusicByTime and AcaFestivalByDate) are used for scenario where the user needs to look for a particular session at the particular date. The first one was checked by the speaker and the tyepOfSession, and the second one was by the festival name and date. 

Both had User input for date or time in string, but both were adjusted differently by the datetime object they are in. 

1. Let’s say that you don't like workshops and you don't like sessions after 7 pm. How would you handle a query for all non-workshop sessions before 7 pm? What is the problem for implementing this query? What ways to solve it did you think of?

answers: 
The potential problem that can happen is datastore query restriction. Datastore requires queries to have inequality filter to be sorted first, and apply the ineqaulity filter afterwards. Session after 7PM needs the sessions to be sorted first before querying sessions by the time. 

To impletment this query, first sort the property with the ineqaulity(session names) first, then filter the inequality for session starttime < 19:00, and then filter the typeOfSession != workshop. 


[1]: https://developers.google.com/appengine
[2]: http://python.org
[3]: https://developers.google.com/appengine/docs/python/endpoints/
[4]: https://console.developers.google.com/
[5]: https://localhost:8080/
[6]: https://developers.google.com/appengine/docs/python/endpoints/endpoints_tool
