# Method

**Source.** eBay completed (sold) listings, pulled through a third-party scraping actor, one pull
per search keyword. Each pull returns the newest N sales matching the keyword.

**What is kept.** `title`, `sold_price_usd`, `ended_at`, `condition`, `keyword`, `item_id`. The
item id lets anyone re-open the original listing and check the row.

**What is dropped, and why.**
- *Shipping.* The field disagreed with reality by an order of magnitude on heavy lots.
- *Seller.* Null on many rows, so no row can be attributed and concentration cannot be measured.
  Where it is present, note that a single seller's listing run can dominate one keyword's newest N.
- *Best-offer flags.* Not exposed, so an accepted offer reads as a fixed price.

**Medians.** Plain median of `sold_price_usd` over the rows in each file, no outlier trimming, so
the number in the README can be reproduced from the CSV in one line of pandas.

**The known bias.** The newest N is a window of days. Seasonality, one auction house dumping a
collection, or a holiday weekend will all move a 30-row median. Treat any single file as a
snapshot, not as a market history.

**Keyword coverage check.** Before a median is published, the share of titles containing the
search word is counted. A treadle pull came back 13/30 on the word "treadle"; the other 17 rows
were parts. That check is why several headline numbers here differ from a naive keyword median.
