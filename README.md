---
module: SQL

level: 1

methods:
  - team
  - pair
  - solo

tags:
  - wip
---

# Academy Exercise: Flights

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.

## Overview

You will write queries to find out information from a provided database containing flight bookings.

## Setup

- Code setup TODO

### Database setup

- Install postgres: TODO: postgres installation notes

- Switch to user `postgres`

`sudo -i -u postgres`

- As user postgres, download the database-creation script:

```
wget https://edu.postgrespro.com/demo-small-en.zip
```

- As user postgres, unzip the database-creation script:

```
unzip demo-small-en.zip
```

It should contain a file called `demo-small-en-20170815.sql` or similar.

- As user postgres, have psql interpret the database-creation script:

```
psql < demo-small-en-20170815.sql
```

You should see messages that are very similar to [this log](log-files/expected-log-from-db-creation.txt)

- Github setup TODO

## Exercise: familiarisation

- Read the following:
  - schema detail https://postgrespro.com/docs/postgrespro/10/apjs03
  - schema diagram https://postgrespro.com/docs/postgrespro/10/apjs02.html
  - schema objects (most importantly, tables and views) https://postgrespro.com/docs/postgrespro/10/apjs04

## Exercise:

Notes:

- In each case, provide the query you use.
- Unless otherwise noted, you should write a single query for each task.

### Queries (existing)

- 010: List all aircraft
- 020: List the seats on the aircraft of type "Cessna 208 Caravan"
- 030: List all cities having more than one airport
- 04x: List all unique destinations for flights from 'Volgograd'...

- 041: first, using only `flights` and `airports`
- 042: then, again using the `routes` view
- Ensure you get the same list of destinations from both approaches.

- 050: List the counts of flights in each status (arrived, cancelled, departed, etc)
- 060: Find the next flight from Yekaterinburg to Moscow, where the time now is given by bookings.now()
- 070: List the 10 most expensive bookings
- 075: List all passengers on the top 3 most expensive bookings
- 080: List the tickets on the booking which has booking reference 521C53
- 090: List the FLIGHTS (not the tickets) included on Antonina Kuznecova's ticket (ticket number 0005432661915)
  - include the flight status, airport names, the model of plane, and fare conditions (business / economy)
- 100: List the seats occupied by Antonina Kuznecova on the various flights that form part of ticket 0005432661915
  - alongside seat number, include date of each flight, departure and arrival cities
- 130: List the booking information for a given booking reference, showing flights, departure time, and seat number if check-in has already taken place.

### Extra query ideas

- 200: List all passengers booked on the (on-time) flight with flight_id '18009'. Include their seat number, if they have checked in, otherwise, leave it null.
- How many seats were not booked on flight X

- 210: List each departure-airport's count of delayed flights.

- 220: List the counts of delayed flights from the city Moscow, breaking it down per airport. (This will be easier with flights_v).

- 230: You must prepare a report for customer services. For each passenger currently booked on a flight which is currently delayed, and which was scheduled to leave at least 1 hour ago* (*according to bookings.now()), list the following:

  - passenger name and id
  - passenger phone number (extracted from the contact_data record) // hint: https://www.postgresql.org/docs/9.3/functions-json.html
  - whether they are travelling business or economy
  - how much their ticket cost
  - the flight number
  - the departing and destination airports
  - how long they have been waiting

-SKIP: find out if the delayed passengers have other flights booked and what the window is

- 240: Report the total costs of tickets purchased on each flight which is currently delayed. Show the flights with the highest totals first.

- 250: list delayed flights which are destined for an airport further West than any Moscow airport. How many are there?

-SKIP: map the destination airports of the delayed flights on a map (use leaflet.js). E.g. export SQL-generated report to json and paste into some scaffolded codepen.

- 260: list the 5 single flight routes which travel the furthest from south to north.

- find all passengers who are the only passenger booked on their respective flights

- List all passenger names and ids who have travelled _directly_ from airport A to airport B within the month of december, 2016. You can assume having a boarding pass means they travelled. Include their seat number.

- List all passenger names and ids who were planning to fly _directly_ from airport A to airport B on the day of D. Include their seat number, if they have checked in.

- Was there a cheaper way for passenger P to accomplish his journey on day D? Write as few queries as possible.

- list all of the airports that airplane with aircraft_code took off from during the month of M.

- for each scheduled flight on day D, list the flight number, the count of checked in passengers, the count of booked tickets which have not yet checked in, and the available capacity that can still be sold.

- list all passengers who have not yet checked in for flight F.

- list the passengers who have travelled the most.

- list the airport with the fewest flights

- Too hard: Passenger X wants to fly from A to B but notices there are no direct flights: write a query to find acceptable flights given the passenger wants to spend no more than M money nor for the total journey duration to be more than D days.

# Presentation task 1

- TODO: try to pick passengers for this task which all have a lot of data associated (multiple flights, different days, return journey, travelling companions, ticket costs, different flight statuses (scheduled, not yet departed, cancelled),

  - who is the person sitting next to, etc.

- Discover as much as you can about your assigned passenger (see below) and prepare a short presentation on this data and the queries you used to obtain it:

- group 1: "DMITRIY KUZMIN"
- group 2: "YURIY MAKAROV"
- group 3: "ALEKSANDR ABRAMOV"
- group 4: "ALIYA MELNIKOVA"
- group 5: "VALERIY KUZNECOV"

# Ideas for more work

## Credits

```

```
