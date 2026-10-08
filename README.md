# Wild Sketch

A responsive one-page landing site for **Wild Sketch**, a community of outdoor
drawing workshops. Built as a team project for the GoIT web development course.

- **Live page:**
  [olesiap.github.io/wild_sketch](https://olesiap.github.io/wild_sketch/)
- **Design:**
  [Figma mockup](https://www.figma.com/design/oWx5k1GaizlUauyom8T8Kw/Wild-Sketch--Copy-)
- **Technical task:**
  [requirements spreadsheet](https://docs.google.com/spreadsheets/d/19NupSCkSmK-grW7dUhLKBMguUYhSm0YZwBsYnSuPf70/edit?gid=0#gid=0)

## Tech stack

- Semantic HTML5 and CSS3 (no frameworks)
- [Vite](https://vitejs.dev/) with
  [vite-plugin-html-inject](https://www.npmjs.com/package/vite-plugin-html-inject)
  for HTML partials
- [modern-normalize](https://github.com/sindresorhus/modern-normalize) for CSS
  normalization
- Google Fonts: Caveat and Tajawal
- SVG sprite for all icons and the logo
- Prettier for code formatting
- GitHub Actions + GitHub Pages for deployment

## Page sections

| Section     | Content                                                       |
| ----------- | ------------------------------------------------------------- |
| Header      | SVG logo, anchor navigation, "Register" link                  |
| Hero        | Main heading, description, "Register" and "Learn More" links  |
| Benefits    | List of three benefits, each with an SVG icon, title and text |
| Gallery     | Flexbox gallery of seven artworks                             |
| Events      | Workshop cards with photo, location, date/time and "Register" |
| Team        | Artist cards with photo, name and role                        |
| Feedbacks   | Testimonials with star ratings                                |
| Register    | Registration form with HTML validation (name, email, comment) |
| Footer      | Logo, anchor links and consumer rights information            |
| Mobile menu | Full-height menu, shown when the `is-open` class is added     |

## Requirements

- **Responsive layout, mobile first**, using `min-width` media queries with
  breakpoints at **375px** (mobile), **768px** (tablet) and **1440px**
  (desktop).
- **Valid, semantic markup** that passes the
  [W3C HTML](https://validator.w3.org/) and
  [CSS](https://jigsaw.w3.org/css-validator/) validators.
- **Optimized images**: raster images have 1x and 2x versions for retina
  screens, and every icon is loaded from one SVG sprite.
- **Hover effects** and a pointer cursor on all interactive elements.
- **Form validation** through HTML attributes:
  - Name and email are required and checked with a `pattern`.
  - The comment is limited to 500 characters.

## Getting started

You need the LTS version of [Node.js](https://nodejs.org/).

```bash
npm install      # install dependencies
npm run dev      # start the dev server at http://localhost:5173
npm run build    # build the production version into dist/
npm run preview  # preview the production build locally
```

## Project structure

```
src/
├── index.html      # page entry point, includes the partials
├── partials/       # HTML markup for each section (header.html, hero.html, ...)
├── css/            # styles: one file per section, plus base, reset and container
├── img/            # raster images (1x and 2x) and sprite.svg
└── public/         # static files copied as is (favicon)
```

Each section has its own partial in `src/partials` and a matching stylesheet in
`src/css`. The partials are inserted into `index.html` with
`<load src="./partials/<name>.html" />`.

## Deployment

Every push to `main` triggers the GitHub Actions workflow
(`.github/workflows/deploy.yml`). The workflow builds the project and publishes
the `dist` folder to the `gh-pages` branch, which GitHub Pages serves.

Work happens in feature branches (for example `header`), which are merged into
`main` through pull requests.
