# UK Crime Checker Project
​
## Overview 
​
This was my second project (built in a group) on the Software Engineering Immersive course at General Assembly.

**UK Crime Checker** is an app where users can search for a category of crime (options included anti-social behaviour, bicycle theft, criminal damage, and many more) and by location using a postcode or the first line of an address.

## Technologies
​
The app was built with:

* React
* Metropolitan Police API - https://data.police.uk/docs/method/crime-categories/
* Bulma
* Mapbox API

## Brief

The app much consume a public API, have several components (at least one classical and one functional) and include a router - with several "pages".

## Deployment

This application was deployed on Heroku at https://ga-sei-project.herokuapp.com/
​
## Getting Started

Use the clone button to download the website source code. From the root directory type 'npm run server' in the terminal. The project will run on localhost:8000.
​
## Website Architecture

The app consists of a search facility that filters through crime categories (i.e. anti-social behaviour, drugs) available on the API and the results are displayed on a map. 
​
<img src="https://i.imgur.com/bSWocIj.png">

### Homepage/Index

The first section of the app has a select/dropdown menu that lists specific crime categories available on the API – the user can select a category and type in a postcode, click the “Filter Crime” button and see a number of found crimes and their placement of the map with red dots as the markers.

The second section consists of a map and demonstrates Mapbox's “Marker”, “Popup” and “Geocoder” features.

### The API
​
The API is updated once every month - it is a complex API with a lot of data, so we had to limit our search to one search filter at a time.  The call limit operates with a 'leaky bucket' algorithm as a controller which allows for infrequent bursts of calls, and allows you to continue to make an unlimited amount of calls over time.

Due to this and our machines not being able to handle too much data (at least not in a user friendly way, having a prolonged waiting time), the shown data was limited to a maximum of 300 results. If the number of results exceeded this maximum number, we could risk having the server crashing with a HTTP 429 error. 
​
Below is an excerpt of code from the Home Page which was built as a classical React component.
​
<img src="https://i.imgur.com/MnVV5lT.png" width= 500px height= 600px>

### Mapbox

After carefully reading the documentation, Mapbox was incredibly easy to implement - it was up and running in no time at all. What has proved to be a more tedious process was turning the coordinates of a certain crime (provided by the API as a string) into actual markers on the map. 
​
The process of rendering the data on the map was made possible by utilising a classical React component using a map function that maps through different categories of crimes provided by the API. The Pop Ups have been placed using the same coordinates.
​
<img src="https://i.imgur.com/jWYCzCI.png" width= 500px height= 600px>

## Wins & Key Learnings

It was a fascinating project - I really enjoyed working with Mapbox and seeing what it's capable of doing. 

My key learning was to read the API and Mapbox's documentation carefully in the planning stages of the project. Documentation gives you all the support and guidance y0ou need - the implementation process is smoother and seamless.

## Future improvements

One of the main challenges was placing the provided coordinates on the map. We had to create a second axios GET request and map through the crimes and associated coordinates. This was new process for us and it took a while to work through.
​
<img src="https://i.imgur.com/RA0704Y.png" height= 200px> 
​
Refactoring the code would help speed up the process of loading the page which - at the moment - is rather slow. The possibility to search through the crimes based on the date and more information on the crime would definitely be a great step forward.
