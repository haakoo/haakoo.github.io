# Don't readme

## Deploying using travis

- user and Organization pages only publish content from the `master` branch
- travis dpl v2 https://docs.travis-ci.com/user/deployment-v2/providers/pages/
- use a different branch for the source e.g. `release`

### how-to

https://medium.com/@mcred/supercharge-github-pages-with-jekyll-and-travis-ci-699bc0bde075

```
master <- generated static site content
release <- Jekyll code to be generated into site
develop <- Branch that contains changes until merged into release
```
