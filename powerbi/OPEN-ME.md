# Opening the Power BI report

`AdelaideRents.pbip` is a Power BI Project: the report (`AdelaideRents.Report`, PBIR format) and the semantic model (`AdelaideRents.SemanticModel`, TMDL) saved as text, so the repo can show every change. Power BI Desktop opens it like a `.pbix`.

## What you need

- Power BI Desktop for Windows, a recent version (2026). Projects and the PBIR report format are standard in current versions. If Desktop is older than about mid 2025, turn on **File, Options and settings, Options, Preview features, Power BI Project (.pbip) save option** and **Store reports using enhanced metadata format (PBIR)**, then restart Desktop.
- The repo folder on the Windows machine. In Parallels the Mac home folder is usually shared as `\\Mac\Home`.

## Open it

1. In Windows, go to the repo's `powerbi` folder and double-click `AdelaideRents.pbip`, or in Desktop use **File, Open report, Browse reports** with the file type set to *Power BI project files (\*.pbip)*.
2. The visuals are empty the first time. Select **Refresh** on the Home ribbon.
   - By default the data is read from the repo's public copy on GitHub (`DataFolder` is `https://raw.githubusercontent.com/cjmuldoon/plotlay-adelaide-rents/main/data/`). If Desktop asks how to connect, choose **Anonymous** and then **Connect**.
   - To read the files from disk instead, go to **Home, Transform data, Edit parameters** and set `DataFolder` to the full path of the repo's `data` folder, **ending with a backslash** (for example `\\Mac\Home\plotlay-adelaide-rents\data\`). Then select **OK** and **Apply changes**.
   - If Desktop warns about privacy levels, choose **Ignore privacy levels** (all the sources are public open data).
3. Check the numbers (below).

If the report was updated while open, close Power BI and reopen the .pbip rather than using Apply external changes.

## Check the numbers after Refresh

After **Refresh**, on **Rise since 2015** (as the report opens):

| Card | Should read |
|---|---|
| Greater Adelaide, 2015 | $319 |
| Greater Adelaide, year to June 2026 | $569 |
| Rise across Greater Adelaide | 78% |
| The middle suburb's rise (%) | 83.3 |

On **Quarter by quarter** the two lines end in June 2026 at $631 (houses) and $513 (flats and units).

## The model

- **Suburbs**: one row per Greater Adelaide suburb (`data/tables/suburbs.csv`): typical new-bond rent in 2015 and the year to June 2026, the rise, for all dwellings, houses and units. Measures: `Rise (%)`, `Rise, houses (%)`, `Rise, units (%)`, `Suburbs compared`, `Median suburb rise (%)`.
- **Quarters**: one row per suburb and quarter (`quarters.csv`), related to Suburbs by `code`. Measure: `Median rent` (the latest quarter when none is picked).
- **Metro**: Greater Adelaide by quarter (`metro.csv`). Measures: `Houses`, `Flats and units`, `Typical rent 2015`, `Typical rent 2026`, `Greater Adelaide rise`.

## The map

The Shape Map on page 1 has its custom map saved inside the report (`AdelaideRents.Report/StaticResources/RegisteredResources/`): Greater Adelaide's suburbs keyed by ABS code, with South Australia's councils round them in a pale ground tone. If it shows the world instead (an older Desktop can ignore a saved map): select it, then **Format visual**, **Visual**, **Map settings**, **Map type: Custom map**, **Add map type**, and choose `..\data\geometry\suburbs.topojson`. If the Shape Map is not in the Visualizations pane, turn it on in **File, Options and settings, Options, Preview features, Shape map visual** and restart Desktop.

## Save a .pbix too

After the refresh, use **File, Save as** with the type **Power BI file (\*.pbix)** to save `powerbi\AdelaideRents.pbix`. It includes the data, so it opens without a refresh.

## Publish (only if you choose to)

Use **Home, Publish**. In the Power BI service, set the semantic model's **Data source credentials** for the GitHub address to **Anonymous**. Scheduled refresh then works with no gateway. **Publish to web** makes a public link, so only use it if you mean the report to be public.

## Shot list for the website and the video

| # | Shot | How | Length |
|---|---|---|---|
| 1 | Rise since 2015 | As it opens | still |
| 2 | Quarter by quarter | As it opens | still |
| 3 | Suburb by suburb | As it opens | still |

Save page images into `powerbi/Screenshots/` (a PDF export of all pages is fine too).
