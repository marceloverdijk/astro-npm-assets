# Welcome to [Astro](https://astro.build)

This repository tries to integrate [`bootstrap-icons`](https://icons.getbootstrap.com/) and [`flag-icons`](https://flagicons.lipis.dev/) (without using `astro-icon`).

`bootstrap`, `bootstrap-icons` and `flag-icons` are installed as `npm` dependency.

In `src/styles/master.scss` scss is imported for `bootstrap`, `bootstrap-icons` and `flag-icons` 
which works for getting the appropriate css in the page.

However this is not sufficient as `bootstrap-icons` requires `woff` files and `flag-icons` requires `svg` files
(which are part of the `npm` dependency in `node_modules`).

Questions:

- How to expose `node_modules/bootstrap-icons/font/fonts/*.woff|woff2` font files to the project as assets?
- How to expose `node_modules/flag-icons/flags/**/.*.svg` svg files to the project as assets?

as now I'm getting:

```
12:35:09 AM [serve]    404                        /flags/4x3/gb.svg
12:35:09 AM [serve]    404                        /flags/4x3/nl.svg
12:35:09 AM [serve]    404             /fonts/bootstrap-icons.woff2
12:35:09 AM [serve]    404              /fonts/bootstrap-icons.woff
```

and they are also not included in the build when running `npm run build`.

Notes: 

- `src/components/Card.astro` is using `bootstrap-icons`: `<i class="bi bi-arrow-right"></i>`
- `src/pages/index.astro` is using `flag-icons`: `<span class="fi fi-gb me-2"></span>`
