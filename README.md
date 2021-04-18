# Steps

* `git init`
* Add a `.gitignore` for `_sites/` and `node_modules/`
* `npm init -y`
* `npm install --save-dev @11ty/eleventy`
* Add a simple `.eleventy.js` config file
* Add a simple `index.html` page
* `npm install --save-dev tailwindcss@latest postcss@latest postcss-cli@latest autoprefixer@latest`
* `npx tailwindcss init --package`
* Add a `tailwind.css` with `@tailwind` entries
* Add `mode` and `purge` to `tailwind.config.js`
* Add scripts to package.json
	* `"build": "rm -rf ./_site && npm run build:eleventy & npm run build:tailwind",`
	* `"build:eleventy": "npx @11ty/eleventy",`
	* `"build:tailwind": "TAILWIND_MODE=build NODE_ENV=production postcss ./tailwind.css --output ./_site/default.css",`
	* `"dev": "rm -rf ./_site && npm run dev:eleventy & npm run dev:tailwind",`
	* `"dev:eleventy": "npx @11ty/eleventy --serve",`
	* `"dev:tailwind": "TAILWIND_MODE=watch NODE_ENV=development postcss ./tailwind.css --output ./_site/default.css --watch"`
* `npm run dev`
	* Builds a minimal Tailwind CSS file and saves it to `./_site/default.css`
* Add the class `text-red-200` to the `body` in `index.html` and save.
	* The class `text-red-200` is added to the CSS, saved to `./_site/default.css` and the browser refreshes.
* Changed the class of the `body` from `text-red-200` to `text-green-200` in `index.html` and save
	* The class `text-green-200` is added to the CSS and saved to `./_site/default.css` but the class `text-red-200` is not removed and the browser refreshes.
* Add `h1 { @apply text-7xl font-bold; }` to `tailwind.css`
	* The class `h1` is added to the CSS and saved to `./_site/default.css` but the browser does not refresh. This is expected as the changes to `tailwind.css` and the generated `./_site/default.css` file are not being watched by Eleventy. A manual browser refresh will show the change.
