# ProPair Challenge

Welcome to the ProPair challenge! This project is meant to be a fun assessment of your Software architecture knowledge, coding skills, resourcefulness and ability to learn new technologies quickly, it also reflects very clolsely the type of tasks you'd be faced with on a daily basis as a ProPair software developer.

### The things we care about ###

* Your ability to follow instructions thoroughly 
* Communication skills if/when clarification is needed
* Code cleanliness and structure (proper code abstraction and reusability, etc)
* Code Tests
* Code Performance

### Deliverables ###

* Access to the source code (to be hosted in your GitHub account)
* Access to working API endpoints
* A screen sharing session where you'll demonstrate the artifacts created by this exercise in your AWS account

### Timeframe ###

We believe 72 hours is a reasonable timeframe to complete this project, please let us know if this doesn't sound reasonable to you.

### The challlenge ###

We want to build an AI-powered crime prediction system for the San Francisco Police Department! As a Software Developer at ProPair you are tasked with creating the platform necessary to consume, parse, store, regularly update and process data from the SFPD crime database.

#### Technical Requirements: ####

* Implement this system using a serverless architecture with [AWS Lambda](https://aws.amazon.com/lambda/)
* AWS Lambda supports multiple programming language runtimes (Node.js 8, Java 8, Python 3.6 and 2.7, .NET 2 and 2.1, Go 1.x, etc) feel free to use the one you are more comfortable with, `but extra points will be awarded if you use Node.js or Python.`
* For data storage you have the following options: Use a relational database (MySQL or Postgres) or a NoSQL database (DynamoDB). `Please explain the reasoning behind your decision.`
* Public endpoints must be protected behind authentication. [Bearer Authentication](https://swagger.io/docs/specification/authentication/bearer-authentication/) is strongly suggested and hard-coding a single token is fine (i.e. no need to create a true 'users' DB table with unique tokens per account).
* Use JSON for all the API endpoints


### Product Specs: ###

* The SFPD crime dataset (police-department-incidents.csv) is hosted at the [Kaggle website](https://www.kaggle.com/san-francisco/sf-police-calls-for-service-and-incidents)
* The dataset must be downloaded and cached locally in the chosen database management system
* A new copy of the dataset must be downloaded and used to refresh the local database every 24 hours since this dataset is constantly updated by the SFPD
* The clients that will consume these APIs may have limited support for special characters, so as part of this data import, make sure to sanitize strings by replacing all special characters (non-alphanumeric) with a dash (-)
* Create an API endpoint that returns all the entries of any given date, such date will be passed as a URL param (e.g. /your_endpoint?date=2018-08-08) Keep in mind that dates in the dataset are in UTC and the SFPD will be querying this report in PST. 
* Create a second API endpoint that upon receiving a search term will return the number of times matching crimes have occurred in the last 30 days, aggregated by day and ordered by date in descending order (again, mind the timezone). 

E.g. 

/your_endpoint?crime=petty+theft

Response:

```
[{
  "crime": "petty theft",
  "date": "2018-08-08",
  "occurrences": 15
},
{
  "crime": "petty theft",
  "date": "2018-08-07",
  "occurrences": 12
}]
```

* Create a third API endpoint that upon receiving a date, will return the different resolutions as aggregated percentages.

E.g.

/your_endpoint?date=2018-08-08

Response:

```
[{
  "resolution": "ARREST, BOOKED",
  "date": "2018-08-08",
  "percentage": "23%"
},
{
  "resolution": "COMPLAINANT REFUSES TO PROSECUTE",
  "date": "2018-08-08",
  "occurrences": "12%"
}]
```

* Assuming a fourth API endpoint that upon receiving a crime, day_of_week and hour_of_day will predict the likelihood of such crime to occur on such day_of_week and hour_of_day anywhere in San Francisco, please explain what would be some techniques/formulas/libraries/other ideas you would use to implement this. For extra credit, go ahead and implement the 4th endpoint (Tip: you don't have to use fancy deep learning techniques to do this, but feel free to if you believe it is the right choice!)

E.g.

/your_endpoint?crime=petty+theft&day_of_week=Sunday&hour_of_day=20

Response:

```
{
  "crime": "pretty theft",
  "day_of_week": "Sunday",
  "hour_of_day": 20,
  "likelihood": "13%"
}
```

# Good Luck! #
