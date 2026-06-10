# pandemic early warning dashboard

a browser-based biosurveillance dashboard that tracks active disease outbreaks globally — with an interactive world map, risk indicators, case timelines, and trend charts. no backend, no dependencies, just one html file.

---

## what it does

it's designed to look and feel like a real epidemiological monitoring tool. you get:

- **global outbreak map** — colour-coded outbreak points (critical / high / moderate / monitoring) with pulse animations showing active spread
- **left panel** — filterable list of active events by threat level, searchable by pathogen name or region
- **risk indicators** per outbreak — R₀ (basic reproduction number), CFR, spread risk score, containment score, cross-border risk, and doubling time
- **event timelines** — chronological progression of each outbreak from detection to current status
- **situation summaries** — plain-english writeups explaining the epidemiology, transmission dynamics, and what makes each outbreak significant
- **global trend chart** — weekly alert volume over 12 weeks / 6 months / 1 year
- **live UTC clock** + alert banner for the top active threat

---

## why i built this

i got interested in how public health agencies like WHO and the US CDC structure their outbreak monitoring — and what a well-designed early warning interface for that kind of data might actually look like. most real biosurveillance dashboards are either paywalled, clunky, or buried in government portals.

this is my attempt at a clean, readable version — the kind of tool that would help someone quickly understand *which* outbreaks are actually alarming and *why*, without needing an epidemiology degree.

the data is fictional (based on real-world pathogen characteristics and historical outbreak patterns) but the metrics — R₀ estimates, CFR ranges, containment scores — are grounded in how these diseases actually behave.

---

## the data model

each outbreak has:

```js
{
  name, pathogen, region, country,
  severity,           // critical / high / moderate / low
  cases, deaths,
  r0,                 // basic reproduction number
  cfr,                // case fatality rate (%)
  doubling,           // doubling time in days
  spreadRisk,         // 0–100 composite score
  containmentScore,   // 0–100
  healthSystemStress, // 0–100
  crossBorderRisk,    // 0–100
  timeline,           // array of { date, text } events
  description         // full situation summary
}
```

---

## stack

html, css, vanilla js. no build step, no libraries, no api calls. open `index.html` and it works.

fonts loaded from google fonts (space grotesk + space mono). that's the only external dependency.

---

## running it

```bash
git clone https://github.com/yourusername/pandemic-dashboard
open index.html
```

or just double-click the file.

---

## what's next

a few things i'd like to add:

- [ ] real data via WHO disease outbreak news api or promed feed
- [ ] exportable snapshot (pdf / png) of the current dashboard state
- [ ] "compare outbreaks" mode — plot two events side by side
- [ ] mobile-responsive map interaction
- [ ] historical archive — browse past outbreak events by year

---

## a note on the data

everything here is synthetic. the pathogens are real (H5N1, cholera, mpox, etc.) and the epidemiological parameters are based on published literature, but the case counts, timelines, and geographic details are invented for demonstration purposes. this is not a public health resource — don't use it for anything that actually matters.

---

built to explore data visualisation for public health and practice designing information-dense dashboards that are still readable.
