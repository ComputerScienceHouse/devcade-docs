# Devcade Documentation

This repo contains or links to all relevant documentation for the Devcade project using docsify. Hosted at: https://devcade.csh.rit.edu/docs#/

All documentation should live in the repo it applies to. If some documentation doesn't fit in any of the projects other repos, it may live here.

# Editing the docs

If something doesn't look right, you can edit any of the docs by going to the hosted site, finding the article that needs editing, and using the "Edit on github" button in the top right corner. Alternatively, you can go to the repo directly and find the relevant doc file. Once there, please make the appropriate edits and open a PR with your changes.

If a new page needs to be added to the sidebar, you should add it to the _sidebar file located at docs/_sidebar.md

If a new repo needs to be linked in, add an alias to the alias section of the index.html file.

For further changes to the docsify site overall, refer to the [docsify documentation](https://docsify.js.org/#/?id=docsify).

# Running locally

Install docsify-cli
```
npm i docsify-cli -g
```

And serve it, the site will then be available at `http://localhost:3000/docs/`
```
docsify serve . --open
```

# Deploying

Upon pushing to the docs branch, a webhook should take care of rebuilding the okd pod.