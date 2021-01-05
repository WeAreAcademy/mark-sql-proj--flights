---
module: SQL

level: 1

methods:
  - team
  - pair
  - solo
---

# Academy Exercise: Flights

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.

## Overview

You will write queries to find out information from a provided database containing flight bookings.

## Pre-reqs

- You have Postgres installed.
- You have a database user which has the same name as your login, and it has permissions to create databases.
- Optional, recommended: You have installed either:
  - [vscode extension `PostgreSQL` by Chris Kolkman](https://marketplace.visualstudio.com/items?itemName=ckolkman.vscode-postgres) or
  - [vscode extension `SQLTools` by Matheus Teixeira](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools) as well as
    - [https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools-driver-pg](SQLTools PostgreSQL/Redshift Driver)
  - or some other means of quickly running queries.

## Setup

### Database setup

- In the terminal, log in as your database user.

- Download [this database-creation script](https://edu.postgrespro.com/demo-small-en.zip).

Tip: If you have `wget` installed, you can do this on the terminal as follows:

`wget https://edu.postgrespro.com/demo-small-en.zip`

- Unzip it

e.g. on the terminal:

```
unzip demo-small-en.zip
```

- Check it contains a file called `demo-small-en-20170815.sql`, or similar.

- Ensure you do not have a database called `demo` which you do not wish to lose - the following step will delete it!

- On the terminal, ensure you are logged in with your normal user.

- On the terminal, have `psql` execute the database-creation script:

```
psql < demo-small-en-20170815.sql
```

This may take a couple of minutes.

- Check there is only one error in the log, and that it concerns the DROP DATABASE statement. (This error will arise because the database doesn't yet exist.)

## Exercise - familiarisation

Familiarise yourself with the database structure by reading the following documents:

- [Schema detail](https://postgrespro.com/docs/postgrespro/10/apjs03)
- [Schema diagram](https://postgrespro.com/docs/postgrespro/10/apjs02.html)
- [Schema objects](https://postgrespro.com/docs/postgrespro/10/apjs04) (most importantly, tables and views)

## Exercise - writing queries:

Notes:

- In each case, provide the query you use.
- Unless otherwise noted, you should write a single query for each task.

### Queries (warm-up)

- 010: List all aircraft in the system

- 020: List the seats on the aircraft of type "Cessna 208 Caravan"

- 030: List all cities having more than one airport

  - List all unique destinations for flights from 'Volgograd'...

- 041: first, using only `flights` and `airports`

- 042: then, again using the `routes` view

  - Ensure you get the same list of destinations from both approaches.

- 050: List the counts of flights in each status (arrived, cancelled, departed, etc)

- 060: Find the "next" flight from Yekaterinburg to Moscow, where "next" is relative to a time given by bookings.now().

- 070: List the 10 most expensive bookings

- 075: List all passengers on the top 3 most expensive bookings

- 080: List the tickets on the booking which has booking reference 521C53

- 090: List the FLIGHTS (not the tickets) included on Antonina Kuznecova's ticket (ticket number 0005432661915).

  - include the flight status, airport names, the model of plane, and fare conditions (business / economy)

- 100: List the seats occupied by Antonina Kuznecova on the various flights that form part of ticket 0005432661915
  - alongside seat number, include date of each flight, departure and arrival cities

### More queries

- 110: List counts of all of the flights in the database for each of the possible statuses (e.g. Arrived:16707, Cancelled:???,... ). Order by status.

- 200: List all passengers booked on the (On Time) flight with flight_id '3122'. Include their seat number if they have checked in, otherwise, leave it null.

- 210: List each departure-airport's count of delayed flights.

- 220: List the counts of delayed flights from the city Moscow, breaking it down per airport. (This will be easier with flights_v).

- 230: You must prepare a report for customer services. For each passenger currently booked on a flight which is currently delayed, and which was scheduled to leave at least 1 hour ago -relative to the time returned by bookings.now(). List the following:

  - passenger name and id
  - passenger phone number (extracted from the contact_data record) // hint [see this documentation.](https://www.postgresql.org/docs/11/functions-json.html)
  - Whether they are travelling business or economy
  - how much their flight cost
  - the flight number
  - the departing and destination airports
  - how long they have been waiting

- 240: For each currently delayed flight, report the total amount spent on it. Show the flights with the highest totals first.

- 250: list delayed flights which are destined for an airport further West than any Moscow airport. How many are there?

- 260: List all routes where the arrival airport is at least 14 degrees further north than the departure airport.

  - Sort the routes to show the most extreme of these journeys, first.
  - Ensure you have at least the following columns:
    - flight_no
    - departure_city
    - arrival_city
    - departure_coordinates
    - arrival_coordinates

- 261: Export your results from task #260 as JSON, and copy-paste them into [this visualiser](https://academy-flight-routes-vis.netlify.app/). (See note at end on exporting results as JSON).

  - Does the visualisation confirm your expectations about these north-south journeys, and their rankings?

- 265: List the ten routes which have planes flying the furthest distance from east to west.

- 266: Export your results from task #265 as JSON\*, and copy-paste them into [this visualiser](https://academy-flight-routes-vis.netlify.app/).

  - Does the visualisation confirm your expectations about these east-west journeys, and their rankings?

- 270: Find the details of the (presumably luxurious) 'On Time' flights which have only one ticket booked on them. For each, list:

* the name of the only passenger
* whether the passenger has checked in yet or not
* how much they paid for the flight
* the model name of the aircraft

- 280: List all passenger names and ids who have travelled _directly_ from Moscow (any airport) to Tambow on the 22nd or 23rd of July, 2017. You can assume having a boarding pass means they travelled. For each traveller, include:

* passenger's name,
* passenger's id,
* passenger's phone number,
* seat number,
* flight number,
* actual departure time,
* departure and arrival airport codes

- 290: List the names and seat numbers of the six passengers who sat in row 45 or 46 of the flight with the flight_id of 30625.

- 300: Find the airport with the fewest scheduled flights.

- 301: On what days of the week, and to where, can you fly out of the airport you found in the previous exercise?

- 310: From which 5 cities can you fly out on a 'Boeing 777-300'?

# Exercise - Presentation:

- Discover as much as you can about your assigned passenger (see below) and prepare a short presentation on this data and the queries you used to obtain it.

You should try to use as few queries as possible to collect the data.

You should include information on at the very least:

- Itinerary, including:
  - locations involved,
  - timings,
  - type of plane,
  - seat,
  - flight statuses
- Summary of cost
- Summary of travel time

### Which passenger should we report on?

- group 1: book_ref: 02BBD2 & passenger_id 7453 048981 (NATALYA POPOVA)
- group 2: book_ref: 0C2FAC & passenger_id 5759 489758 (OLGA VOLKOVA)
- group 3: book ref: D25BBC & passenger_id 0420 062045 (NATALYA IVANOVA)
- group 4: book ref: 8A450F & passenger_id 1038 607499 (NAZIYA KAZAKOVA)
- group 5: book ref: 82ABCD & passenger_id 0741 149706 (PAVEL ZAKHAROV)

## Exporting results as JSON

First, run your query.

If you have SQLTools installed (see pre-reqs section of this document), each query's results view will have a large `EXPORT` button. Click it and select "Save results as JSON". It'll prompt you for where to save the JSON file.

If you are instead using Chris Kolkman's PostgreSQL extension, after running your query you should see at the very top of the window a little save icon. Click it and choose JSON. If you have multiple results sets it will ask you which set of rows you wish to export. On choosing one, it will export the relevant JSON to a new text window.

## Credits

- These exercises use the ["Demo Database 'Airlines'"](https://postgrespro.com/docs/postgrespro/10/demodb-bookings) from [Postgres Professional](https://postgrespro.com/).
