# Benzinga Calendar API v2

## abstract

This document provides information about Calendar Data access on Benzinga.com via API

## Resource

### GET/calendar

All calendar endpoint

http(s)://api.benzinga.com/api/v2/*Calendar Type*?*Parameters*

## Return Types

Data will be returned in XML or JSON based on the the Accept Header


````
Accept: application/json
```

```
Accept: application/xml
```

If no accept header is set the data will be returned in yaml.


## Parameters

### All Calendars

| Parameter | Required | Type | Format/Options | Default | Description |
| --- | --- | --- | --- | --- | --- | 
| page |  NO |  INT | | 0 |  The page offset. |
| pagesize | NO | INT | | 50 | The number of results returned. Limit 1000. |
| parameters[date] | NO |  STRING | YYYY-MM-DD | | The date to query for calendar data.  Shorthand for date_from and date_to if they are the same.  Defaults for latest. |
| parameters[date_from] | NO | STRING | YYYY-MM-DD | | Date to query from point in time |
| parameters[date_to] | NO | STRING | YYYY-MM-DD | | Date to query to point in time |
| parameters[importance] | NO | INT | 1-5 | | The importance level to filter by.  Uses Greater Than or Equal To the importance indicated. |
| parameters[sortorder] | NO | STRING | ASC / DESC | DESC | The sort order of records returned by Date. Accepts 1 and -1 as ASC and DESC respectively. |
| parameters[tickers] | NO | STRING | T[,...] | | One or more ticker symbols separated by a comma.  All calendar accept this parameter.  Ignored by Economics. |
| parameters[updated] | NO |  INT | 1440777968 | | The records last Updated Unix timestamp (UTC).  This will force the sort order to be Greater Than or Equal to the timestamp indicated |
| token | YES | STRING | | | Client API Token |

