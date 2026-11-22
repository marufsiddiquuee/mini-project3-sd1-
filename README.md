# Country Explorer

This is my mini project (MP3 + MP4) for CSE-2340 Software Development 1 at IIUC. It is a one-page website where you can look up countries, filter them, and save the ones you like.

Live site: https://marufsiddiquuee.github.io/mini-project3-sd1-/

## What it does

- Loads country data (name, flag, capital, region, population) from the REST Countries API
- Search by country name
- Filter by region and sort by name or population
- Shows a loading state, an error message with a retry button, and a "no countries found" message
- Save button on each card. Saved countries show up in the Saved section and stay there after refreshing the page (localStorage)
- Works on phone and desktop, with a navbar that turns into a menu button on small screens

## Built with

- HTML
- Tailwind CSS (from the CDN)
- JavaScript (fetch, async/await, array methods, localStorage)
- REST Countries API v5

## How the code is organised

Everything is in `index.html`.

- `fetchAllCountries()` gets the data from the API. The free plan only gives 100 countries per request, so it loads page by page.
- `normalize()` turns the API data into a simpler object that the rest of my code uses.
- `getVisibleCountries()` does the search, filter and sort on a copy of the data, so the original list is never changed.
- `readSaved()` and `writeSaved()` handle localStorage. Reading is inside a try/catch so broken saved data does not crash the page.
- The country list is also cached in localStorage for 24 hours, because the API has a monthly request limit.

## Running it on your computer

1. Download or clone this repo
2. Get a free API key from restcountries.com
3. Put your key in the `API_KEY` line near the top of the script in `index.html`
4. Add `localhost` and `127.0.0.1` to the allowed origins for your key
5. Open the folder in VS Code and start it with Live Server (opening the file directly will not work because the API blocks requests without a website address)

## Problems I ran into

- The REST Countries API changed and now needs a key, so my first version stopped loading data. I switched to v5 and added the key.
- The API only returns 100 countries at a time, so I had to add paging.
- The key only works for websites listed in its allowed origins, so I had to add my GitHub Pages address there.

## Author

YOUR NAME: Md. Maruf Siddique 
Student ID: C253085 
