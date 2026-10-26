# Grounded Expectations: How Reliable Is Your Airline?
Author: Maddie Gentry

Question: How reliable are the selected airlines, based on cancellations and late arrivals?
Reader: A corporate travel manager comparing airline and destination options.
One row: One BTS carrier code at one destination airport in one month.
Period: January 2018–August 2026 (104 months). Overall totals use all available months. Year comparisons involving 2026 use January–August in each year; September–December selections show earlier available years only.

## Public links
- Website: https://maddieggentry.github.io/grounded-expectations/
- Tableau: https://public.tableau.com/app/profile/maddie.gentry/viz/FDAIIProject2Tableau/AirlineReliabilityDashboard

## Files
- `index.html`: report, recommendation, four findings and charts, methodology, and website/Tableau agreement table.
- `dashboard.html`: interactive dashboard with date, month, airline, destination, comparison-window and COVID-year controls.
- `app.js`: CSV parsing, browser calculations, filters, charts, exports and presentation interactions.
- `styles.css`: shared responsive styles, airport-themed presentation and reduced-motion alternatives.
- `data.csv`: prepared analysis data used by both pages and Tableau; 90,785 rows, 10 columns, 10 selected airlines, 266 airports.
- `audit.json`: cleaning counts and coverage metadata.
- `source.zip`: unchanged uploaded BTS archive, containing `Airline_Delay_Cause.csv` and `Download_Column_Definitions.xlsx`.
- `README.md`: file inventory, provenance and definitions.
- `.nojekyll`: serves the website as ordinary static files on GitHub Pages.
- `assets/AA.png`, `AS.png`, `B6.png`, `DL.png`, `F9.png`, `G4.png`, `HA.png`, `NK.png`, `UA.png`, `WN.png`: American, Alaska, JetBlue, Delta, Frontier, Allegiant, Hawaiian, Spirit, United and Southwest identification logos, respectively.

## Source and preparation
Bureau of Transportation Statistics, Airline On-Time Statistics and Delay Causes:
https://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp?pn=0000

The uploaded source archive contains 201,168 monthly records and 21 columns. Retain AA, AS, B6, DL, F9, G4, HA, NK, UA and WN. Exclude other carrier codes, 50 selected-carrier rows missing scheduled-flight or cancellation totals, and zero-scheduled-flight records. Preserve missing delay counts as blank; do not replace them with zero. The source counts are preserved under readable field names. 112 prepared monthly records lack delay counts.

These selected carrier series do not represent all domestic flights or every service sold under each airline brand. Separate regional codes are excluded. Carrier coverage can change, and Hawaiian has no August 2018 record. No missing periods are imputed. Comparisons are descriptive and do not adjust for routes, weather or operating conditions.

## Definitions and baseline
- Scheduled flights: sum of scheduled_flights, including cancelled scheduled arrivals.
- Cancelled flights: sum of cancelled_flights.
- Cancellation rate: sum(cancelled_flights) / sum(scheduled_flights).
- Airlines represented: distinct airline_code count.

All-month baseline: 40,993,471 scheduled; 785,261 cancelled; 1.92% cancellation rate; 10 airlines. The same values were independently read from the author's Tableau screenshot and are recorded separately in the agreement table.

Delayed flights arrive at least 15 minutes late. Delay rate divides delayed flights by scheduled flights in records with known delay counts. Average delay divides arrival_delay_minutes by delayed_flights over those same known records. Missing-delay records remain in cancellation totals. A flight delayed before cancellation is recorded as cancelled rather than as a late arrival; these monthly aggregates do not show status histories.

Affected flights combines cancellations and late arrivals only in records with known delay counts; its scheduled-flight comparison uses the identical subset. It counts flights, not travelers. Other scheduled flights are not labelled on-time because diversions are not separately measured here.

Airport charts rank up to 15 airports with at least 100,000 scheduled flights within the selected records. The minimum is fixed and affects only airport charts. Rates are ratios of summed counts, never averages of row percentages.

## Interaction
Dashboard filters update charts and totals. Logos open an independent airline boarding pass using the selected dates, month, destination and COVID setting; opening a boarding pass does not change dashboard filters or totals. The airline dropdown controls dashboard-wide airline filtering. Year comparisons have their own equal-month scope, explained beside the chart. Departures-style tiles summarize dataset selections, not live flights. The reading tracker measures scroll distance. Animations respect reduced-motion settings.

## Logo provenance
Nine airline logos were retrieved from https://images.kiwi.com/airlines/64/{IATA}.png. Southwest's corrected official heart logo is from https://www.southwest.com/swa-resources/images/trademarks/sw-heart.png. Logos are locally stored identification marks owned by their respective airlines; no affiliation is implied.

## Running locally
Serve this folder through a static web server; direct file opening cannot fetch CSV in most browsers. No build process or framework is required.
