# Charlie: The Citizen Journalist App

> When news events happen, it becomes prohibitively expensive to pay for video of those events through the few organizations that control those images. 

_However there are thousands of phones with HD video camera settings in any given city that are in close proximity. Why not pay them directly to send us proper news video?_

  

# Getting Started

  

>  ### Prerequisites

+ `X_code` and `ios-simulator`
  You will need to have a Mac to download the XCode from the app store. 

+ `Node.js`
  You will need to install Node.js using the following link in order to access the API locally. 
  https://nodejs.org/en/download/
- The backend API is written in javascript (node) and uses the  [`express`](https://github.com/expressjs/express)  framework. It interfaces with a  [`postgres`](https://www.postgresql.org/)  database using  [`bookshelf`](http://bookshelfjs.org/)  and  [`knex`](http://knexjs.org/). We also interact with a custom  [`scheduling server`](https://github.com/miketerpak/scheduler)  for handling delayed events and notifications.

>  ### Installing
+ Clone the IOS app git repository in XCode using command `https://github.com/Citizen-Charlie/iOS-App.git` or `git@github.com:Citizen-Charlie/iOS-App.git` if working on a ssh remote server. 
+ Nothing needs to be configured. Simply build the app in the XCode. For a fully functional app to be simulated, using your iPhone instead of the simulator.
  
>  ### Running Locally
+ Clone the API git repository in some code editors (our recommendation is Visual Studio Code) using command `https://github.com/Citizen-Charlie/API.git`
+ You need to set up your local psql database
    + create a new database `CREATE DATABASE [your database name]`
    + Add this extension to your database `CREATE EXTENSION postgis`;
    + In the API code, find a file `db.json`and change the configuration according to your local database. For example, `host: localhost`
    + In your terminal, go to the `sql` folder, run `psql -h localhost -p [your port where psql is running] -d [your database name] -U [username if exists] -f index.sql`. This will create all the tables for you.
    + Then run `data.sql` in the same way. This will insert some basic values such as the client credentials to the database.
    + After everything is done, run `npm start` to start the server.
  
>  ### Warranty
The API is last tested in November 2020. This is tested in Postman.

  

# Testing

  We don't provide a test suite for this app. 


# Deployment
+ The production system lives on AWS. To obtain access (AWS credentials), you will need to contact Mr. Greg Morey, our client. 
+ A user can build their own EC2 server on AWS using the runnable API backend for deployment. 
+ No addons needed.
+ No CI/CD offered.
  

# Technologies used

+ X_code

+ Objective-C

+ The ADRs is appended in this README file.

  

# Contributing

 + A new developer needs to get access to the Github repository and the AWS console.
 + No specific style, testing, or process conventions.
 + For more background information: https://uncteamx.netlify.app/

  

# Authors

+ Fresconews developers
+ Team X from UNC: Hanqi Zhang, Tenghao Huang, Kyuyeon Kim
+ Bryan Dunbar, Elmir Kouliev

 
# License
+ we need to ask our clients
  

# Acknowledgements

> We would like to express our deepest appreciation to Elmir Kouliev and Bryan Dunbar for their technical assistance and to our client Greg Morey for his support and encourage.

# ADRS


>  ### Summary

In order to make Citizen Charlie a mobile iOS app and compatible with the legacy code from our clients, we decide to use Xcode 12 as our IDE, PostgreSQL as our database, AWS as our backend service, and Objective C as our programming languages.

>  ### Problem
We are trying to create apps on both iOS and android platforms. Our main problem is about how to refactor the application and also make it compatible with legacy code and APIs.  

>  ### Constraints
 There are prototypes of all functionalities, but together we have a lot version problems since the app is written five years ago. The other thing is that our choices on tools are limited, since the legacy code has already predefined things that we could use. Time is another problem for us. If we want to move forward from the legacy code, we may not have enough time to implement all the functionalities.

>  ### Options

* [React Native] https://reactnative.dev/ – a JavaScript framework for writing real, natively rendering mobile applications for iOS and Android.
* [Xcode 12] https://developer.apple.com/xcode/ - an integrated development environment (IDE) for macOS
* [Visual Studio Code] https://code.visualstudio.com/ - a free source-code editor made by Microsoft for Windows
* [JavaScript] https://www.javascript.com/ -  a scripting or programming language that allows you to implement complex features on web pages
* [PostgreSQL] https://www.postgresql.org/ - a powerful, open source object-relational database system
* [Objective C] 
* AWS: EC2 server, S3 bucket, Lambda, Cloudfront


>  ### Rationale

Chosen option: `Xcode 12` & `Objective C]`& `PostgreSQL`, because our plan shift from developing both ios and android apps to particularly focusing on iOS app. Considering the legacy code we got from our clients, we decided to use Xcode 12 as our IDE and use Objective C as the programming language. For backend, we chose PostgreSQL. On one hand, the tools we choose are all popular tools in the industry. They all demonstrated to be strong and useful tools. On the other hand, since our project is strongly client-oriented, we made above decisions as required by our clients. Finally, our clients wanted the app to be deployed on AWS.

Design documentation is important to enable people understanding the decisions later on.
* Xcode is the only supported IDE for iOS app
* Legacy API are mostly based on PostgreSQL
* Legacy code are mostly based on Objective C
