# Corporate Logos API v1

## Abstract

This document provides an outline to the Benzinga.com API access to Corporate Logos.

## Resource

### GET /api/v1/logos

```
http(s)://api.benzinga.com/api/v1/logos?<Parameters>
```

## Return Types

Data will be provided in XML or JSON form.  Upon success, it will return data for specific logos.  XML or JSON may be selected by passing the proper header.  XML is current default.  


| JSON Accept Header |
---
| Accept: application/json |


## Parameters

| Parameter | Required | Type | Format/Options | Default | Description |
|---|---|---|---|---|---|
| token | YES | STRING |  | - | Client API Token |
| symbols | YES | STRING |  | - | A list of ticker symbols separated by a comma(,). Limit 50 tickers per request. |
| filters | NO | STRING |  | - | A list of client-specific filters to be applied. Filters are separated by a comma (,). |

## Result Data

| Result | Type | Expected Format | Null | Description |
|---|---|---|---|---|
| logos | STRUCT |  | Y |  |


### logos STRUCT

| Result | Type | Expected Format | Null | Description |
|---|---|---|---|---|
| security | STRUCT |  | N | Security Identifier |
| created |  |  |  |  |
| updated | INT | 123456789 | N | Last updated timestamp, UTC |
| files | STRUCT |  | Y | List of files available for the listed security |

### security STRUCT

| Result | Type | Expected Format | Null | Description |
|---|---|---|---|---|
| symbol | STRING |  | N |  |
| exchange | STRING |  | N |  |
| name | STRING |  | N | Name of Security |
| cik | STRING |  | Y |  |
| isin | STRING |  | Y |  |
| valoren | STRING |  | Y |  |
| cusip | STRING |  | Y |  |

### files STRUCT

| Result | Type | Expected Format | Null | Description |
|---|---|---|---|---|
| original | STRING |  | Y | Original File |
| 90&times;60_white | STRING |  | Y | Resized 90&times;60, full color with a white or transparent background |
| 90&times;60_grayscale | STRING |  | Y | Resized 90&times;60, grayscaled with a white or transparent background |
| &lt;custom_filter&gt; | STRING |  | Y | One or most custom filters |


## Examples

### XML Return Value

#### URL:

```
https://api.benzinga.com/api/v1/logos?token=<REPLACE_WITH_YOUR_TOKEN>&symbols=AAPL,F
```

##### curl:

```
curl -X GET -H "Accept: application/xml" -H "Cache-Control: no-cache" "https://api.benzinga.com/api/v1/logos?token=<REPLACE_WITH_YOUR_TOKEN>&symbols=AAPL%2CF"
```
#### Returned:

```
<?xml version="1.0" encoding="utf-8"?>
<result>
    <logos is_array="true">
        <item>
            <security>
                <symbol>AAPL</symbol>
                <cik>320193</cik>
                <name>Apple Inc. - Common Stock</name>
                <exchange>NASDAQ</exchange>
            </security>
            <created>1393219926</created>
            <updated>1482345595</updated>
            <files>
                <original>https://cdn1.benzinga.com/files/ticker-logos/std/apple.png</original>
                <_90x60_white>https://cdn1.benzinga.com/files/imagecache/90x60_white/ticker-logos/std/apple.png</_90x60_white>
                <_90x60_grayscale>https://cdn1.benzinga.com/files/imagecache/90x60_grayscale/ticker-logos/std/apple.png</_90x60_grayscale>
            </files>
        </item>
        <item>
            <security>
                <symbol>F</symbol>
                <cik>906361</cik>
                <name>Ford Motor Company Common Stock</name>
                <exchange>NYSE</exchange>
            </security>
            <created>1393008835</created>
            <updated>1482345662</updated>
            <files>
                <original>https://cdn3.benzinga.com/files/ticker-logos/std/f_.png</original>
                <_90x60_white>https://cdn3.benzinga.com/files/imagecache/90x60_white/ticker-logos/std/f_.png</_90x60_white>
                <_90x60_grayscale>https://cdn3.benzinga.com/files/imagecache/90x60_grayscale/ticker-logos/std/f_.png</_90x60_grayscale>
            </files>
        </item>
    </logos>
</result>
```


### JSON Return Value

#### URL:

```
https://api.benzinga.com/api/v1/logos?token=<REPLACE_WITH_YOUR_TOKEN>&symbols=AAPL,F
```

#### curl:

```
curl -X GET -H "Accept: application/json" -H "Cache-Control: no-cache" "https://api.benzinga.com/api/v1/logos?token=<REPLACE_WITH_YOUR_TOKEN>&symbols=AAPL%2CF"
```

#### Returned: 

```

{
  "logos": [
    {
      "security": {
        "symbol": "AAPL",
        "cik": "320193",
        "name": "Apple Inc. - Common Stock",
        "exchange": "NASDAQ"
      },
      "created": 1393219926,
      "updated": 1482345595,
      "files": {
        "original": "https://cdn1.benzinga.com/files/ticker-logos/std/apple.png",
        "90x60_white": "https://cdn1.benzinga.com/files/imagecache/90x60_white/ticker-logos/std/apple.png",
        "90x60_grayscale": "https://cdn1.benzinga.com/files/imagecache/90x60_grayscale/ticker-logos/std/apple.png"
      }
    },
    {
      "security": {
        "symbol": "F",
        "cik": "906361",
        "name": "Ford Motor Company Common Stock",
        "exchange": "NYSE"
      },
      "created": 1393008835,
      "updated": 1482345662,
      "files": {
        "original": "https://cdn3.benzinga.com/files/ticker-logos/std/f_.png",
        "90x60_white": "https://cdn3.benzinga.com/files/imagecache/90x60_white/ticker-logos/std/f_.png",
        "90x60_grayscale": "https://cdn3.benzinga.com/files/imagecache/90x60_grayscale/ticker-logos/std/f_.png"
      }
    }
  ]
}

```