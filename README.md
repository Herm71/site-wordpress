# [@Herm71](https://github.com/Herm71)'s WordPress WP-ENV Dev Environment

This workflow assumes you have [Docker](https://www.docker.com/) running and [npm](https://www.npmjs.com/) installed.

If [wp-env](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-env/) is not installed globally, the command `npm install` will install it locally and provide a `wp-env` script for running `wp-env`.

This setup maps `wp-content/themes` to a separate working directory outside this environment. This enables working on themes outside this `root` directory, which is my preferred development workflow.

## Recommendations

- [Block editor](https://developer.wordpress.org/block-editor/how-to-guides/themes/block-theme-overview/) currently requires the [Gutenberg plugin](https://github.com/WordPress/gutenberg)
- [Theme Unit Test](https://codex.wordpress.org/Theme_Unit_Test), a WordPress export (WXR) file that you can import into a WordPress installation to test your theme

## Features

- `.wp-env.json` that maps theme development directory *outside* this `root` environment
- `.htaccess` file for adjusting site (eg., "pretty permalinks")
- [WordPress Importer](https://wordpress.org/plugins/wordpress-importer/) plugin for importing default content (such as [Theme Unit Test](https://codex.wordpress.org/Theme_Unit_Test)).
- [Theme Check](https://wordpress.org/plugins/theme-check/) plugin for testing theme against the latest WordPress theme standards and practices

## Install

- clone this repo to a directory (eg., `wp-env-site-root/`) and `cd` into it
- run command: `npm install` or `npm i`
- edit `.wp-env.json` to add your dev theme directory as described [below](#edit-wp-env.json)
- run command: `npm run wp-env start` (or simply `wp-env start` if you already have `wp-env` installed globally)
- visit your new site at [http://localhost:8888/](http://localhost:8888/)
- login to the [Dashboard](http://localhost:8888/wp-admin)
    - default username: `admin`
    - default password: `password`
- activate development theme via Dashboard->Appearance->Themes

Your working environment directory setup should look like this after build:

```text
wp-env-site-root/
  |---.wp-env.json
  |---.htaccess
  |---mu-plugins/
  |---plugins/
    |---theme-check/
    |---wordpress-importer/
  |---mu-plugins/
  |---themes/ # any themes pulled in via git in .wp-env.json. Not dev theme.
dev-theme-dir/
  |--[dev theme directory location set up in .wp-env.json]
```

## Edit wp-env.json

Edit the `"mappings":"wp-content/themes":` value in `.wp-env.json` to point to your theme development directory. Your theme will be loaded but not activated in the site's dashboard.

If you were working on a plugin you could add an additional key for `"wp-content/plugins":` to the `"mappings":` array to point to a development plugin directory.
