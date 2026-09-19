# ebay-sold-comps

**570 real eBay completed sales across 9 collectible categories, as CSV.** Title, sold price, end
date, condition, the search keyword that found it, and the eBay item id. Pulled 2026-09-16 to
2026-09-19, nothing simulated, nothing rounded.

eBay's own completed-sales view is behind a login, holds about 90 days, and cannot be exported.
Every "what is it worth" article you can find quotes *asking* prices instead, which is why a press
story will say a pattern is "worth $25,000" while the same pattern's completed sales sit at $18.99.
This repo is the boring version: what people actually paid, with the date on every row.

## What is in here

| file | n | median | range | sold between |
|---|---:|---:|---|---|
| `data/castiron.csv` | 30 | $50.00 | $1.00 - $225.00 | 2026-09-18 |
| `data/corningware-cw_cornflower.csv` | 30 | $20.75 | $0.99 - $138.50 | 2026-09-18 |
| `data/corningware-cw_generic.csv` | 60 | $15.00 | $6.00 - $879.99 | 2026-09-18 |
| `data/corningware-cw_marj.csv` | 30 | $18.99 | $12.00 - $45.00 | 2026-09-02 - 09-18 |
| `data/fiesta.csv` | 30 | $25.00 | $8.95 - $168.99 | 2026-09-17 - 09-18 |
| `data/hotwheels-lot.csv` | 30 | $39.48 | $6.49 - $898.00 | 2026-09-18 |
| `data/hotwheels-redline.csv` | 30 | $44.50 | $5.00 - $231.50 | 2026-09-18 |
| `data/lecreuset.csv` | 30 | $75.00 | $20.00 - $295.00 | 2026-09-16 - 09-18 |
| `data/pyrex.csv` | 30 | $17.28 | $6.60 - $335.00 | 2026-09-18 |
| `data/retro-video-games-cib.csv` | 60 | $99.88 | $8.00 - $1,500.00 | 2026-08-23 - 09-18 |
| `data/retro-video-games-lots.csv` | 60 | $32.50 | $2.39 - $1,149.99 | 2026-09-03 - 09-18 |
| `data/sewing-machines-featherweight.csv` | 30 | $257.75 | $6.43 - $699.00 | 2026-09-16 - 09-18 |
| `data/sewing-machines-generic.csv` | 60 | $94.99 | $5.00 - $999.00 | 2026-09-14 - 09-18 |
| `data/sewing-machines-treadle.csv` | 30 | $52.50 | $1.00 - $680.00 | 2026-09-15 - 09-18 |
| `data/sterling.csv` | 30 | $128.25 | $13.00 - $3,432.49 | 2026-09-18 |

Columns: `title, sold_price_usd, ended_at, condition, keyword, item_id`.

## Four things the rows show that the internet gets wrong

1. **On a boxed game, the cardboard is the item.** Same SNES title: a loose cartridge off a
   pick-your-game listing **$5.99**, the same cartridge inside a 42-game bulk lot **$8.33**
   ($350.00 / 42), complete in box ungraded **median $99.88** (n=55), graded WATA 9.0 **$899.00**.
   The box and manual are about **17x** the cartridge.
2. **A "lot" is usually not a lot.** 12 of the 60 newest *retro video game lot* sales were single
   cartridges with the word *lot* in the title for search traffic (median $4.96), and 8 more were
   brand-new emulator handhelds. They drag the raw median of that search to $32.50. The largest
   sale in the whole pull, $1,149.99, was a 250-pack pallet of new consoles.
3. **Volume is a discount, not a premium.** Where the same object sells both ways, the per-piece
   ladder runs singles > small lots > big fixed-price lots > big auction lots. Measured on 45
   completed war-nickel sales: singles $4.60, lots of 3-6 $3.70, big fixed lots $3.05, big auction
   lots $2.88, against a live melt floor of $3.77 a coin. Past roughly ten pieces in one listing
   the seller is under the metal before eBay's 13.25% and postage.
4. **The furniture is worth more than the machine.** Treadle sewing machines: the median row in
   `sewing-machines-treadle.csv` is $52.50 and the word "treadle" appears in only 13 of the 30
   titles a keyword search returns, because the search fills up with **drawer knobs, belts and
   irons**. A 1948 Singer Featherweight, a machine you can carry in one hand, medians **$257.75**.

## Read this before you quote a median

- **The window is days, not 90.** The source returns the *newest* N completed sales, so 30 rows
  with a 90-day filter is often 1-3 days of that market, not a quarter. The `sold between` column
  above is the real window.
- **Sort the titles by hand.** A keyword pull is not a category. Every headline number here was
  recomputed after reading the 30-60 titles one by one. On the retro-video-game *lot* search that
  correction was worth about 40%: 20 of 60 rows were not vintage lots at all, and the raw $32.50
  median describes single cartridges and new hardware more than it describes a collection.
- **Ignore any shipping field you see elsewhere.** On one 66-car Hot Wheels lot the shipping value
  came back lower than the postage quoted on a single car, so shipping is not published here.
- **One sale is not a price.** Two copies of Super Metroid closed the *same day* at $399.00 and
  $474.99. A boxed SNES DOOM went $199.99 on 09-12 and $132.00 on 09-18.

## Per-category write-ups

Each pull has a human-readable guide with the full ladder, the traps, and what to check in hand:

- [Vintage Pyrex](https://flipworth.silentdirectivellc.com/guides/vintage-pyrex-value)
- [Vintage CorningWare](https://flipworth.silentdirectivellc.com/guides/vintage-corningware-value)
- [Retro video games](https://flipworth.silentdirectivellc.com/guides/retro-video-games-value)
- [Vintage sewing machines](https://flipworth.silentdirectivellc.com/guides/vintage-sewing-machine-value)
- [Cast iron skillets](https://flipworth.silentdirectivellc.com/guides/cast-iron-skillet-value)
- [Fiestaware](https://flipworth.silentdirectivellc.com/guides/fiestaware-value)
- [Sterling silver flatware](https://flipworth.silentdirectivellc.com/guides/sterling-silver-flatware-value)
- [Vintage Hot Wheels](https://flipworth.silentdirectivellc.com/guides/vintage-hot-wheels-value)
- [Vintage Le Creuset](https://flipworth.silentdirectivellc.com/guides/vintage-le-creuset-value)

## License

CC0 1.0. Public domain. Use the rows in a paper, a spreadsheet, a pricing model, a YouTube video,
whatever. Attribution welcome, not required. Corrections by issue or PR: if a row is misclassified,
say which `item_id` and why.

## Browser copy

The same files, with the per-category medians rendered as a table, are served at
<https://flipworth.silentdirectivellc.com/data/> (schema.org `Dataset` markup, CC0, no signup).
