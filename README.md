# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

- # Movie App

A movie discovery app built with React and Vite. Browse popular movies, search for titles, and save favorites to revisit later.

## Features

- Browse popular movies from [The Movie Database (TMDB)](https://www.themoviedb.org/).
- Search movies by title.
- Add and remove movies from your favorites.
- Keep favorites between visits using browser `localStorage`.
- Navigate between the home and favorites pages.
- Responsive movie poster grid.

## Tech Stack

- React 18
- Vite
- React Router
- Plain CSS
- TMDB API

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (which includes npm)
- A TMDB API key

### Install and run

```bash
npm install
npm run dev
```

Open the local URL printed by Vite in your terminal.

### Configure TMDB

Add your TMDB API key to the `API_KEY` constant in `src/services/api.js`:

```js
const API_KEY = "your_tmdb_api_key";
```

The app uses this key in browser requests, so it is visible to users. For a production deployment, route TMDB requests through a backend or serverless function instead of exposing a private credential in the client.

## Available Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server. |
| `npm run build` | Create a production build in `dist/`. |
| `npm run preview` | Preview the production build locally. |
| `npm run lint` | Run ESLint. |

## Project Structure

```text
.
├── index.html
├── public/
│   └── vite.svg
└── src/
    ├── assets/                 # App assets
    ├── components/
    │   ├── MovieCard.jsx       # Movie poster and favorite control
    │   └── NavBar.jsx          # App navigation
    ├── contexts/
    │   └── MovieContext.jsx    # Shared favorites state and persistence
    ├── css/                    # Global and component/page styles
    ├── pages/
    │   ├── Favorites.jsx       # Favorites page
    │   └── Home.jsx            # Popular movies and search
    ├── services/
    │   └── api.js              # TMDB API requests
    ├── App.jsx                 # Routes and shared app layout
    └── main.jsx                # React application entry point
```

## How It Works

- `main.jsx` mounts the React application and enables browser-based routing.
- `App.jsx` defines the `/` home route and `/favorites` route, and wraps the app in `MovieProvider`.
- `Home.jsx` loads popular movies when opened and submits search requests through the API service.
- `MovieCard.jsx` renders each movie and uses the shared context to toggle its favorite status.
- `MovieContext.jsx` provides favorite data and actions across pages and saves changes in `localStorage`.
- Styles are organized under `src/css/`, with global rules in `index.css` and feature-specific styles in separate files.

## Data and Privacy

Movie data and poster images are provided by TMDB. Favorites are stored locally in the current browser and are not synced across devices. Clearing the browser's site data will remove saved favorites.

