# beer-yo-ass-backend

## How do I get this ?
Your IDE ([IntelliJ](https://www.jetbrains.com/idea/), [Eclipse](https://eclipse.org/), [Spring Tool Suit](https://spring.io/tools)) should be able to clone a project from Github.
It should be easy to find information regarding how to do that for your chosen IDE.
It's also possible to download the project as a .zip [here](https://github.com/mbook/SpringBootMVC/archive/master.zip).

## How do I run this ?
You have to have postgres downloaded on your machine and a db called HBV with username "postgres" and password "postgres" <br />

the tables are made automatically <br /> 
This project is setup using [Maven](https://maven.apache.org/what-is-maven.html) as a dependency manager, so if your IDE does not manage that, or you don't have it installed you can look [here](https://maven.apache.org/install.html) for further information.
When all the dependencies are downloaded, you can run the project by running the ``main()`` method in the class ``Application`` and then enter [localhost:8080](http://localhost:8080) into the address bar of your favorite web browser.


### Populating the beer database
You have to have installed a couple of python packages
```$xslt
pip install psycopg2
pip install selenium
pip install bs4
```
You have to have firefox.

Then you need to go into the scraper folder and run
```$xslt
python vinbud_scraper.py
```

Then you have to turn on your postgres database server, with user:postgres, pw:postgres, and create a database named beer-yo-ass

Then go into database folder and run
```$xslt
python createTables.py
python insertData.py
```

## Apinn
note, this application is not secure, maybe we will implement a secure app later.
<br />
Every respone is a String unless other is written.
### get beers
send a get request to 
<br />
/beers
<br />
to get a list of all the beers.

### get a beer
send a get request to 
<br />
/beers/beer
<br />
to get the following information about one beer
<br />
beerId, name, 
linkToVinbudin, 
(float) alcohol, 
taste (e.g. lager, IPA),
(int) volume (in ml),
(float) stars (out of 5),
(int) price (kr.)

### login
send a post request to 
<br />
/login/{username}/{password}
<br />
if the username and password match the response will be (boolean) true otherwise false.
<br />
### signup
send a post request to 
<br />
/signup/{username}/{password}
<br />
if the username is not taken, the response is (boolean) true otherwise false.
### comment
send a post request to 
<br />
/comment/{username}/{beer}/{title}/{comment}/{stars}/
<br />
username is the user logged in, 
beer is the beer being commented on,
title is the title of the comment,
comment is what the user writes about the beer,
stars (float) how many stars out of 5 the user rates the beer.
<br />
response will be (boolean) true if comment was saved otherwise false.