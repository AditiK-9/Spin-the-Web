# 🎰 Spin the Web

A casino-style spin-the-wheel that sends you to a random corner of the internet. Land on a slice to see live data from public APIs, then click through to the site.

Built with plain HTML, CSS and JavaScript in a **single file** (`index.html`), with no frameworks or build step.

## Features

- Animated wheel drawn on an HTML `<canvas>`, with an easing spin that slows to a stop
- 18 websites on the wheel, from Wikipedia and NASA to neal.fun and Radio Garden
- Live data fetched from public APIs when you land on certain slices (marked with a ★)
- A "Take me there!" button that opens the site you landed on
- Bright, casino-style design with blinking lights and a glowing ring
- Responsive layout that works on mobile

## Live data

| Site | Source | What it shows | Key needed? |
|---|---|---|---|
| Wikipedia | Wikipedia REST API | A random article title and summary | No |
| NASA APOD | NASA APOD API | Today's astronomy picture title and description | Yes |
| Hacker News | Hacker News Firebase API | One of the current top stories | No |
| Open Library | Open Library API | A random book and its author | No |
| Spotify Charts | Spotify Web API | A featured playlist | Yes |
| Duolingo | None | A random language suggestion from a built-in list | No |

The remaining slices simply link to their websites.

## Getting started

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/spin-the-web.git
cd spin-the-web
```

### 2. Add your API keys (optional)

Open `index.html` and replace the placeholders near the top of the `<script>` section:

```javascript
const NASA_KEY    = 'YOUR_NASA_KEY_HERE';
const SPOTIFY_ID  = 'YOUR_SPOTIFY_ID_HERE';
const SPOTIFY_SEC = 'YOUR_SPOTIFY_SECRET_HERE';
```

- **NASA:** get a free key at [api.nasa.gov](https://api.nasa.gov)
- **Spotify:** create an app at the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)

Without keys, the wheel still works. The NASA and Spotify slices just won't show live data.

### 3. Run it

Open `index.html` in your browser, or serve the folder with any static web server (for example IIS).

## Hosting on IIS

1. Install IIS and enable **Static Content**.
2. Copy `index.html` into `C:\inetpub\wwwroot\`.
3. Open `http://localhost` in your browser (or whichever port your site uses).

## Security note

API keys placed in front-end JavaScript are visible to anyone who views the page source. **Never commit real keys to a public repo**, and never put a Spotify client secret in browser code on a public site. For anything beyond a personal project, move those requests to a small backend.

## Project structure

```
spin-the-web/
├── index.html   # HTML, CSS and JavaScript in one file
└── README.md
```

## How it works

1. `drawWheel()` paints each slice, emoji and label onto the canvas.
2. Clicking **SPIN IT!** picks a random slice and animates the rotation with `requestAnimationFrame`.
3. When the wheel stops, the result card is filled in and `fetch()` calls the matching API (if the slice has one).
4. The response is displayed under the site name, and the button links to the destination.

## Built with

- HTML5 Canvas
- CSS (custom properties, gradients, keyframe animations)
- Vanilla JavaScript (`fetch`, `async/await`)
- Google Fonts: Fredoka One and Nunito

## Ideas for the future

- Add more sites and APIs
- Move API calls to a small backend so keys stay private
- Let users add their own slices
- Add sound effects when the wheel spins
