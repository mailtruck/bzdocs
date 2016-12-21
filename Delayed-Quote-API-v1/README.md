# Delayed Quote API v1

## Abstract

A delayed quote feed.

## Connection 

Connect using the following URL Structure:

```
http://api.benzinga.com/api/v1/quoteDelayed?<PARAMETERS>
```

### Authentication Parameters

```
token=<unique API token key>
// Unique api-key given to partner
```

### Security Lookup Parameters

Only a single lookup parameter is allowed.

Max 50 identifiers per lookup.

```
symbols=<SYMBOLS>
// Symbols are accepted with the format:
// SYMBOL
// EXCHANGE:SYMBOL
// Symbols without exchange will assume a US equity
isin=<ISIN>
// Comma separated list of ISIN identifiers
cik=<CIK>
// Comma separated list of CIK identifiers

```

## Examples

Set an accept header to specify the format for returned data. You can choose either XML and JSON.

### JSON Return Value:

#### URL:

```
http://api.benzinga.com/api/v1/quoteDelayed?symbols=AAPL&token=<REPLACE_WITH_YOUR_TOKEN>
```

#### curl:

```
curl -X GET -H "Accept: application/json" -H "Cache-Control: no-cache" "http://api.benzinga.com/api/v1/quoteDelayed?symbols=AAPL&token=<REPLACE_WITH_YOUR_TOKEN>"
```

#### Returned:

```
{
  "quotes": [
    {
      "security": {
        "symbol": "AAPL",
        "cik": "320193",
        "valoren": "908440",
        "name": "Apple Inc. - Common Stock"
      },
      "quote": {
        "date": "2016-12-21T15:16:33.707-05:00",
        "open": 116.8,
        "high": 117.4,
        "low": 116.78,
        "previousClose": 116.95,
        "change": 0.1699,
        "changePercent": 0.15,
        "fiftyTwoWeekHigh": 119.86,
        "fiftyTwoWeekLow": 89.47,
        "currency": "USD",
        "last": 117.1199,
        "tradingHalted": false,
        "volume": 13516405,
        "previousCloseDate": "2016-12-20T16:00:00.000-05:00"
      }
    }
  ]
}
```

### XML Return Value:

#### URL:

```
http://api.benzinga.com/api/v1/quoteDelayed?symbols=AAPL&token=<REPLACE_WITH_YOUR_TOKEN>
```

#### curl:

```
curl -X GET -H "Accept: application/xml" -H "Cache-Control: no-cache" "http://api.benzinga.com/api/v1/quoteDelayed?symbols=AAPL&token=<REPLACE_WITH_YOUR_TOKEN>"
```

#### Returned:

```
<?xml version="1.0" encoding="utf-8"?>
<result>
    <quotes is_array="true">
        <item>
            <security>
                <symbol>AAPL</symbol>
                <cik>320193</cik>
                <valoren>908440</valoren>
                <name>Apple Inc. - Common Stock</name>
            </security>
            <quote>
                <date>2016-12-21T15:22:00.770-05:00</date>
                <open>116.8</open>
                <high>117.4</high>
                <low>116.78</low>
                <previousClose>116.95</previousClose>
                <change>0.16</change>
                <changePercent>0.14</changePercent>
                <fiftyTwoWeekHigh>119.86</fiftyTwoWeekHigh>
                <fiftyTwoWeekLow>89.47</fiftyTwoWeekLow>
                <currency>USD</currency>
                <last>117.11</last>
                <tradingHalted></tradingHalted>
                <volume>13703931</volume>
                <previousCloseDate>2016-12-20T16:00:00.000-05:00</previousCloseDate>
            </quote>
        </item>
    </quotes>
</result>
```