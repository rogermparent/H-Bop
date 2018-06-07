# H-Bop

**Yeah, I know, *another* Hugo+Gulp Boilerplate**

This is a boilerplate for using [Hugo](https://gohugo.io/) [Gulp](https://gulpjs.com/) 4 together. Oh yeah, it uses some [Webpack](https://webpack.js.org/) too. It's derived from [Victor Hugo](https://github.com/netlify/victor-hugo) from the guys at Netlify, but hacked up and updated to suit my personal tastes.

H-Bop uses [SCSS](https://sass-lang.com/) stylesheets and runs them through [PostCSS](http://postcss.org/) for some optimizations.

[Babel](https://babeljs.io/) is used for CSS and JavaScript compiling/transpiling.

The example theme and content, at least for now, are copied from the Hugo theme [Minimal](https://github.com/calintat/minimal) and build with [Bulma](https://github.com/jgthms/bulma).

This project is released under the [MIT license](LICENSE). Please make sure you understand its implications and guarantees.

## Usage

### Installation

Just clone this repo and use it as a starter.

### Development

While developing your website, use:

```bash
npm start
```

or

```bash
gulp server
```

or for developing your website with `hugo server --buildDrafts --buildFuture`, use:

```bash
npm run start-preview
```

or

```bash
gulp server-preview
```

Then visit http://localhost:3000/ *- or a new browser windows popped-up already -* to preview your new website. BrowserSync will automatically reload the CSS or refresh the whole page, when stylesheets or content changes.

### Static build

To build a static version of the website inside the `/dist` folder, run:

```bash
npm run build
```

To get a preview of posts or articles not yet published, run:

```bash
npm run build-preview
```

See [package.json](package.json#L7) or the included gulp file for all tasks.

## Structure

### site

Everything in here will be built with hugo

**site/content:** Pages and collections - ask if you need extra pages

**site/data:** YAML data files with any data for use in examples

**site/layouts:** This is where all templates go

**site/layouts/partials:** This is where includes live

**site/layouts/index.html:** The index page

**site/static:** Files in here ends up in the public folder

### src

Files in here are processed by the gulp asset pipeline and moved into dist.

While your Hugo site should reference their final destinations, Hugo never 
actually sees these- They're pumped straight to dist in parallel with the build.

**src/css:** styles.scss will be compiled into dist/styles.css

**src/js:** app.js will be compiled to /app.js with babel

**src/images:** All files will be attempted to be optimized and sent to dist

## Environment variables

To separate the development and production *- aka build -* stages, all gulp tasks run with a node environment variable named either `development` or `production`.

You can access the environment variable inside the theme files with `getenv "NODE_ENV"`. See the following example for a conditional statement:

    {{ if eq (getenv "NODE_ENV") "development" }}You're in development!{{ end }}

All tasks starting with *build* set the environment variable to `production` - the other will set it to `development`.

## Deploying to Netlify

- Push your clone to your own GitHub repository.
- [Create a new site on Netlify](https://app.netlify.com/start) and link the repository.

Now Netlify will build and deploy your site whenever you push to git.
