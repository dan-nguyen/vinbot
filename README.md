# vinbot

A fast, single-file Tesla VIN decoder. Paste any Tesla VIN and get a full breakdown of the vehicle — model, trim, drivetrain, range, Autopilot hardware, production sequence, and more.

**[Try it →](https://dan-nguyen.github.io/vinbot/)**

## Features

- Decodes all Tesla models: Model S, 3, X, Y, Cybertruck, Roadster, Cybercab, Semi
- Full legacy Model S support (2012–2020) with year-specific decoding
- Derived fields: Trim, Drivetrain, Seating, EPA Range, Supercharger generation, Market region
- HW1 / HW2.5 / HW3 / HW4 Autopilot hardware inference based on production sequence and plant
- Production sequence visualization — per-plant progress bar and global year-range estimate
- VIN check digit validation
- Color-coded VIN breakdown with WMI / VDS / VIS section labels
- Shareable URLs via `?vin=` query parameter
- Dark mode (default), with toggle — preference saved to localStorage
- No dependencies, no build step — one HTML file

## Browser extensions

A Chrome extension and Tampermonkey userscript that auto-detect Tesla VINs on any webpage and show a decoded popup on click are available at **[dan-nguyen/vinbot-userscripts](https://github.com/dan-nguyen/vinbot-userscripts)**.

## Supported Models

| Code | Model | Years |
|------|-------|-------|
| S | Model S | 2012–present |
| 3 | Model 3 | 2017–present |
| X | Model X | 2015–present |
| Y | Model Y | 2019–present |
| C | Cybertruck | 2023–present |
| R | Roadster | 2008–2012 |
| A | Cybercab | 2025–present |
| T | Semi | 2022–present |

## Usage

Open `index.html` directly in any browser — no server needed.

To share a decoded VIN, copy the URL after pasting one in. The VIN is preserved in the `?vin=` parameter.

## VIN Structure

| Positions | Section | Description |
|-----------|---------|-------------|
| 1–3 | WMI | World Manufacturer Identifier |
| 4–9 | VDS | Vehicle Descriptor Section |
| 10–17 | VIS | Vehicle Identifier Section |

Position 9 is a check digit calculated per NHTSA/ISO 3779. Position 10 encodes model year, position 11 the assembly plant, and positions 12–17 the sequential production number.

## Sources

- Tesla Model S/3/X/Y/Cybertruck service manuals
- [Wikipedia — Vehicle Identification Number](https://en.wikipedia.org/wiki/Vehicle_identification_number)
- Community VIN research
