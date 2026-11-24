# Hotel Room Tracker

A single-page, mobile-first tracker for hotel room check-ins and check-outs. No build step, no server: open `index.html` in any browser.

## Features

- **Weekly grid**: dates and days across the top, one row per room. Cells show check-in, check-out, staying, vacant, or a same-day check-out and check-in.
- **Guest and company**: each booking has a guest name and an optional company name. The company shows as a coloured-initials thumbnail and label.
- **Share bookings**: the Share button on the Bookings list builds a neat text summary: a header with totals, then each room in its own block (guest, company, stay, status) separated by ruled lines. Copy it and paste it into any chat or email. 
- **Week-aware bookings list**: the Bookings list shows only the week selected in the grid (a stay that spans two weeks appears in both). Use the week arrows to see earlier or later bookings. Share always summarizes the week shown.
- **Same-day stays**: check-in and check-out can be the same date (tap "Same day" under Nights). It shows as a SAME DAY cell, counts as 0 nights (tallied separately as same-day), blocks the room only for that day, and counts the room as occupied on that date in Vacancy.
- **Check-in / check-out times and clashes**: bookings can carry optional times. Where a guest leaving and one arriving (or a same-day stay) overlap in the same room, the grid cell gets a red outline with a warning mark, the booking card and Share message say who it clashes with, and the booking form warns as you type (you can still save). Missing times use the standard check-in/check-out times in Settings (default 12:00 pm / 11:00 am). Times are included in the Excel export and import.
- **Checked out status**: on the check-out day (or later, if missed) the booking card and day sheet show a Check out button. A booking shows "Checked out" only after you tap it (Undo is available); until then it shows "Leaving today". The "Leaving today" count only includes guests not yet checked out. The time is saved and included in the Excel export and import.
- **Checked in status**: on the arrival day a booking shows "Checked in" only when you tap the Check in button; otherwise it shows "Arriving today". The "Yet to check in" count follows the same rule. Check-out works the same way with its own button.
- **Nights booked**: a card at the top of Tracker shows nights booked in the week shown, plus a From/To calendar picker for any period (both dates included). Each shows occupancy as a share of room-nights and follows the room filter.
- **One-tap check-in**: on the day of arrival, tap Check in on the booking (or in the day sheet). The time is recorded, the label changes from Arriving today to Checked in, and the week grid shows a tick. Undo is one tap away. The check-in time is included in the Excel export and import.
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
