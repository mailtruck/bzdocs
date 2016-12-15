#Benzinga.com News Feed Rest API v2

##Abstract

This document provides an outline to the Benzinga.com API access for News Data.

##Connection

Connect using the following URL structure:

http://api.benzinga.com/api/v2/channels
http://api.benzinga.com/api/v2/news?\<Parameters>
http://api.benzinga.com/api/v2/news/\<id>?\<Parameters>

**Authentication Parameters**

[token] = <unique API token key>
// unique api-key given to partner

##Data

Data will be provided in XML or JSON form.  Upon success, it will return event data for specific calendars.  XML or JSON may be selected by passing the proper header.  XML is current default.  

JSON Header:

Accept: application/json

## Endpoints:

api/v2/channels

api/v2/news

api/v2/news-top-stories

## Options

* token

  Client API Key

* pageSize

  The number of results returned.  Default 15.  Limit 100.
* page

  The page offset.  Default 0.

* displayOutput

  Options: full, abstract, headline

  Default is headline only.

* Optional Parameters
  * date

    Format: YYYY-MM-DD

    The date to query for calendar data.  Shorthand for date_from and date_to if they are the same.

    Defaults for latest.
  * dateFrom

    Format: YYYY-MM-DD

    Date to query from point in time and sorted by published date.

  * dateTo

    Date to query to point in time and sorted by published date.

    Format: YYYY-MM-DD
  * lastId

    The last ID to start paging from and sorted by and sorted by the last updated date.

  * updatedSince

    The last updated unix timestamp (UTC) to pull and sort by.

  * publishedSince

    The last publish unix  timestamp (UTC) to pull and sort by.

  * tickers

    Multiple ticker may be separated by a comma.  

  * channel

    Multiple channels may be separated by a comma



Data Definitions


[

   {

       id:               // Internal ID of Channel

       name:              // Name of Channel
   },

]

**api/v2/news**

**api/v2/news-top-stories**

[

   id:         // ID of article

   author:     // Author Name

   created:    //Datetime in ISO format: Wed, 15 Oct 2014 08:59:20 -0500

   updated:    // Datetime in ISO format: Wed, 15 Oct 2014 09:04:20 -0500

   title:      // Title of Article

   teaser:     // Teaser of content

   body:       // Body of content

   url:        // URL of article

   image: [

       {

            size:   // Sizes are thumb, small, large

            url:   // URL to image

       }

   ]

   channels: [

      {

           name: <CHANNEL>

      },

   ]

   stocks: [

      {

           name: <SYMBOL>

      },

   ]

   tags: [

      {

           name: <TAG>

      },

   ]

]
