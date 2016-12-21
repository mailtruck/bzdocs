# Delaed Quote API v1

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
http://api.benzinga.com/api/v1/quoteDelayed?symbol=AAPL&token=<REPLACE_WITH_YOUR_TOKEN>
```