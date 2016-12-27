# XML / RSS Document Definitions
## Standard Feed

###RSS Spec

RSS / Channel &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The article wrapper to conform with rss specifications

Item &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;An article

* Title &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The title/headline of the article

* Description &nbsp;&nbsp;&nbsp;&nbsp;The summary of the article
* Link &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The URL on the website to find this article
* PubDate &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Date the article was published on
* Category &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Any entity/ticker/channel/tag associated with the article
	* domain:stock­symbol &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ticker Symbol AND ISIN Code
	* domain:sector &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Channel / Category / Tag
	* domain:http://www.ben...&nbsp;&nbsp;The link back to the specified category
	* domain:publisher &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Article Publisher
* Dc:creator &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Author
* Guid &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Globally Unique Identifier ­ The article ID

##Extended Feed
###RSS Spec (above) with Custom Namesapce
BZ Namespace

* bz:id &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Globally Unique Identifier ­ The article ID without domain
* bz:revisionid The article’s unique Revision ID. Will change on updates.
* bz:revisiondate Date the article was last updated on
* bz:ticker Ticker symbol. Identify primary with attr primary=”1”
	* sentiment Rate Scale ­4 (very bearish) to 4 (very bullish). Only
available for stories with a single primary ticker.
	* exchange The exchange the symbol is referencing.
	* isin The ISIN code of the ticker.
* bz:action Indicates article status. Only used with “delete” articles.
* bz:type The aritlce type. Current press­release or story
	* bz Filter option for Benzinga.com feature articles.
	* pro Filter option for Benzinga Pro realtime news and headlines.

##Removed Feed
###RSS Spec + BZ Custom Namespace
RSS / Channel &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The article wrapper to conform with rss specifications

Item &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;An article

* Title &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This should be blank.
* PubDate &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Date the article was removed on.
* Guid &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Globally Unique Identifier / ID of the item to be removed.
* bz:id &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The ID of the item to be removed
* bz:action &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Action set to ‘deleted’.

##Sample Data
###Basic Feed
```
<?xml version="1.0" encoding="utf­8" ?>
<rss version="2.0" xml:base="http://www.benzinga.com/partner­export/rss.xml"
xmlns:dc="http://purl.org/dc/elements/1.1/">
	<channel>
		<title></title>
		<link>http://www.benzinga.com/tradestation­export/rss.xml</link>
		<description></description>
		<language>en</language>
		<item>
			<title>ARTICLE TITLE</title>
			<link>http://www.benzinga.com/news/1234512345/07/12/story</link>
			<description>Lorem ipsum dolor sit ...</description>
			<category domain="http://www.benzinga.com/analyst­ratings/price­target">Price Target</category>
			<category domain="http://www.benzinga.com/analyst­ratings">Analyst Ratings</category>
			<category domain="stock­symbol">PPO</category>
			<category domain="stock­symbol">AAPL</category>
			<category domain="stock­symbol">US73179V1035</category>
			<category domain="sector">Analyst Color</category>
			<category domain="sector">Price Target</category>
			<category domain="sector">Analyst Ratings</category>
			<category domain="publisher">Benzinga</category>
			<category domain="bullbear">­1</category>
			<pubDate>Mon, 05 Mar 2012 15:14:22 +0000</pubDate>
			<dc:creator>John Doe</dc:creator>
			<guid isPermaLink="false">1234512345 at http://www.benzinga.com</guid>
		</item>
	</channel>
</rss>
```

###Extended Feed
```
<?xml version="1.0" encoding="utf­8" ?>
<rss version="2.0" xml:base="http://www.benzinga.com/partner­export/rss.xml"
xmlns:dc="http://purl.org/dc/elements/1.1/"
xmlns:bz=”http://www.benzinga.com/feed­ns­bz/1.0/”>
	<channel>
		<title></title>
		<link>http://www.benzinga.com/tradestation­export/rss.xml</link>
		<description></description>
		<language>en</language>
		<item>
			<title>ARTICLE TITLE</title>
			<link>http://www.benzinga.com/news/1234512345/07/12/story</link>
			<description>Lorem ipsum dolor sit ...</description>
			<category domain="http://www.benzinga.com/analyst­ratings/price­target">Price Target</category>
			<category domain="http://www.benzinga.com/analyst­ratings">Analyst Ratings</category>
			<category domain="stock­symbol">PPO</category>
			<category domain="stock­symbol">AAPL</category>
			<category domain="stock­symbol">US73179V1035</category>
			<category domain="sector">Analyst Color</category>
			<category domain="sector">Price Target</category>
			<category domain="sector">Analyst Ratings</category>
			<category domain="publisher">Benzinga</category>
			<category domain="bullbear">­1</category>
			<pubDate>Mon, 05 Mar 2012 15:14:22 +0000</pubDate>
			<dc:creator>Aaron Wise</dc:creator>
			<guid isPermaLink="false">1234512345 at http://www.benzinga.com</guid>
			<bz:id>1234512345</bz:id>
			<bz:revisionid>2569908</bz:revisionid>
			<bz:revisiondate>Mon, 05 Mar 2012 15:49:27 +0000</bz:revisiondate>
			<bz:ticker primary="1" sentiment=”4”>CI</bz:ticker>
			<bz:ticker primary="0">AAPL</bz:ticker>
			<bz:action></bz:action>
		</item>
	</channel>
</rss>
```

###Removed Feed
```
<?xml version="1.0" encoding="utf­8" ?><rss version="2.0"
xml:base="http://www.benzinga.com/feed­bzdeleted.xml" xmlns:dc="http://purl.org/dc/elements/1.1/"
xmlns:bz=”http://www.benzinga.com/feed­ns­bz/1.0/”>
	<channel>
		<title>Benzinga.com Deleted Stories</title>
		<link>http://www.benzinga.com/feed­bzdeleted.xml</link>
		<description></description>
		<language>en</language>
		<item>
			<title></title>
			<guid isPermaLink="false">4086265 at http://www.benzinga.com</guid>
			<pubDate>Sunday 17 November 2013 12:10 PM</pubDate>
			<bz:action>deleted</bz:action>
			<bz:id>4086265</bz:id>
		</item>
	</channel>
</rss>
```