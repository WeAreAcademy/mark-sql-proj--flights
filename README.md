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

You will write queries to find out information from a provided flight bookings database.

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
- Deployment setup TODO

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

- List all aircraft
- List the seats on the aircraft of type "Cessna 208 Caravan"
- List all cities having more than one airport
- List all destinations for flights from Volgograd
- List the counts of flights in each status (arrived, cancelled, departed, etc)
- Find the next flight from Yekaterinburg to Moscow, where the time now is given by bookings.now()
- List the 10 most expensive bookings
- List the tickets on the booking which has booking reference 521C53
- List the flights included on Antonina Kuznecova's ticket (ticket number 0005432661915)
- List the seats occupied by Antonina Kuznecova on the various flights that form part of ticket 0005432661915
- Create a booking (a transaction with multiple inserts (into bookings, tickets, ticket_flights))
- Add a boarding pass for someone's ticket on a certain flight (model checking in)
- List the booking information for a given booking reference, showing flights, departure times, seat number if a booking has already taken place.

### Extra query ideas

- Find all passengers booked on flight X
- List the count of delayed flights from X to Y (will be easier with flights_v) where X and Y are Yekaterinburg and Moscow.

- Explain why booking X is so expensive
- How many seats were not booked on flight X

- List all of the passenger names booked on flight F. Include their seat number, if they have checked in.

- List all passenger names and ids who have travelled _directly_ from airport A to airport B within the month of december, 2016. Include their seat number, if they have checked in.

- List all passenger names and ids who were planning to fly _directly_ from airport A to airport B on the day of D. Include their seat number, if they have checked in.

* Was there a cheaper way for passenger P to accomplish his journey on day D? Write as few queries as possible.

* list all of the airports that airplane with aircraft_code took off from during the month of M.

* for each scheduled flight on day D, list the flight number, the count of checked in passengers, the count of booked tickets which have not yet checked in, and the available capacity that can still be sold.

* list all passengers who have not yet checked in for flight F.

* Too hard: Passenger X wants to fly from A to B but notices there are no direct flights: write a query to find acceptable flights given the passenger wants to spend no more than M money nor for the total journey duration to be more than D days.

# Ideas for more work

## Credits

```

```
