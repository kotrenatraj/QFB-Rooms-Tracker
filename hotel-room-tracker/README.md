# Hotel Room Tracker

A single-page, mobile-first tracker for hotel room check-ins and check-outs. No build step, no server: open `index.html` in any browser.

## Features

- **Weekly grid**: dates and days across the top, one row per room. Cells show check-in, check-out, staying, vacant, or a same-day check-out and check-in.
- **Guest and company**: each booking has a guest name and an optional company name. The company shows as a coloured-initials thumbnail and label.
- **Fast entry**: tap a vacant cell to book it, tap a booked cell to see or edit the stay. Quick "nights" buttons set the check-out date.
- **Double-booking guard**: overlapping stays for the same room are blocked. Back-to-back stays are allowed.
- **Vacancy tab**: pick any date and see which rooms are vacant (by room number) and which are occupied.
- **Settings tab**: set the total number of rooms and, optionally, the room numbers.
- **Excel export and import** (`.xlsx`): move bookings between devices. Import accepts `.xls` or `.xlsx` and asks before replacing data.
- **Phone friendly**: bottom tab bar, no sideways scrolling, swipe to change week, light and dark themes.

## Run it

```sh
open index.html          # or double-click it
# or serve it locally
python3 -m http.server 8000
```

## Host it on GitHub Pages

Repository **Settings > Pages > Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`. The page is then available at `https://<user>.github.io/<repo>/`. Open that link on a phone and use the browser's "Add to Home Screen".

## Data

Bookings and settings are stored in the browser's `localStorage`, so they stay on one device. Use **Export** on one device and **Import** on another to move them. The export workbook has three sheets: `Bookings`, `Weekly Occupancy` and `Settings`. Import reads the `Bookings` sheet (columns: Room, Guest, Company, Check-in, Check-out; files without a Company column still import) and the `Settings` sheet.

## Notes

- Excel handling uses [SheetJS](https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js) from a CDN, and fonts come from Google Fonts. The tracker itself works offline once loaded, but Export and Import need the SheetJS script.
- Dates are stored as `YYYY-MM-DD` in the device's local time zone.
