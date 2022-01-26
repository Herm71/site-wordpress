# WP-ENV Dev environment

WordPress development environment using [wp-env](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-env/) that maps `wp-content/themes` to a separate working directory outside this environment. This enables working on themes outside this `root` directory, which is my preferred development workflow.

**mapped to root:**

- `.htaccess` for customizing permalinks, etc.
- `wp-content/plugins` because I'm not developing a plugin at the moment. Were I to begin developing a plugin I would re-map this elsewhere.
- `wp-content/mu-plugins` just because.