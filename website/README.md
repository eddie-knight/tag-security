# TAG Security Website

This directory contains a [Hugo](https://gohugo.io) web site published via [Netlify](https://www.netlify.com/) to <https://tag-security.cncf.io/>.

When the `main` branch of this repo is updated a fresh build and deploy of the website is executed. Recent Netlify builds and deployments are listed at <https://app.netlify.com/sites/tag-security>.

Add content by adding Markdown files to directories identified in the [Makefile](./Makefile) include list.

Update layouts for each content type in [./layouts](./layouts/).

Configuration is set in [config.toml](./config.toml).

## Setting up a local dev instance

To set up a local dev environment make sure you have [Hugo Extended](https://gohugo.io/installation/linux/#editions), [npm](https://www.npmjs.com/), and [rsync](https://github.com/RsyncProject/rsync) installed, then run the following:

```bash
git clone git@github.com:cncf/tag-security.git
cd tag-security/website/
make deps
npm install
```

Then run the site using `npm run serve`. To have the site run locally with a functioning local search, run `npm run serve:with-pagefind`.

### Cleanup

To cleanup website build files prior to commit - run `make clean`.
