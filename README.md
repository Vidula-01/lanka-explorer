# Lanka Explorer

**Group name:** Lanka Explorer Team  *(replace with your group name)*
**Tagline:** Lanka Explorer – Discover the Pearl of the Indian Ocean
**Live link:** *(add here if you deploy to Netlify or GitHub Pages)*

## Group members and roles

| Member | Role |
| --- | --- |
| Member Name 1 | Project Lead |
| Member Name 2 | Content Lead |
| Member Name 3 | Data Lead |
| Member Name 4 | UI Lead |

## Project description

Lanka Explorer is a front-end web app that helps travellers discover and plan a trip around Sri Lanka.
It is built with plain HTML, CSS, JavaScript and JSON, plus three free web APIs.

## Destinations used on the website

`data/destinations.json` holds **10 destinations** (Heritage, Beach, Nature and Wildlife).
The website uses **3** of them, which are the ones marked `"active": true`:

| Destination | Category | Image |
| --- | --- | --- |
| Sigiriya Rock Fortress | Heritage | images/sigiriya.jpg |
| Ella | Nature | images/ella.jpg |
| Yala National Park | Wildlife | images/yala.jpg |

The other 7 (Galle Fort, Arugam Bay, Jaffna, Matara, Nuwara Eliya, Kandy, Trincomalee) are kept in the
JSON file and `images/` folder but are **not shown**. `loadDestinations()` in `js/app.js` skips any record
with `"active": false`. To show one on the site, change its `active` value to `true`; no HTML changes are needed.

## Features

- Five linked pages with the same semantic header, navigation and footer
- Responsive layout (Flexbox and Grid) from 375 px to 1280 px+, with a mobile menu
- Cards generated from JSON; search (name, district, description), category filter and sort
- Details page driven by the URL (`details.html?id=1`), with a "not found" message for a wrong id
- Live weather and 3-day forecast, entry fee in LKR, and interactive maps
- Loading spinners and friendly error messages for every API
- My Trip planner saved in localStorage, with traveller count and USD/LKR totals
- Dark mode saved in localStorage
- Enquiry form with JavaScript validation (including a 500-character message limit)

## APIs used

Open-Meteo (weather), Frankfurter (USD to LKR rate), Leaflet + OpenStreetMap (maps). See `API-NOTES.md`.

## How to run

The site must be opened through a web server, because `fetch()` cannot read `data/destinations.json`
from a `file:///` address.

1. Open the `lanka-explorer` folder in Visual Studio Code.
2. Install the **Live Server** extension (Ritwick Dey).
3. Right-click `index.html` and choose **Open with Live Server** (http://127.0.0.1:5500/).

Alternative: run `python3 -m http.server 5500` inside the folder and open http://localhost:5500/.

## Week 02 specificity answer

The checkbox-label rule is `#enquiry-form fieldset label`, not `fieldset label`, because of specificity.
The earlier rule `#enquiry-form label { font-weight: 600; }` contains an id, so it scores (1,0,1).
`fieldset label` scores only (0,0,2), which is lower, so it would lose and the checkbox labels would stay bold.
`#enquiry-form fieldset label` scores (1,0,2), which beats `#enquiry-form label` and lets the labels use normal weight.

## Lighthouse scores (fill in after running Chrome DevTools → Lighthouse, Mobile)

| Page | Performance | Accessibility | Best practices | SEO |
| --- | --- | --- | --- | --- |
| Home | | | | |
| Details | | | | |

## Notes

- Image file names are lowercase with hyphens. `nuwara.jpg` from the supplied images is a Kandy collage, so it is saved as `images/kandy.jpg`.
- Entry fees are in USD. Yala is the foreign adult park fee (USD 25); Kandy's Temple of the Tooth is about LKR 2,000. Sources differ, so re-check before publishing.
