Blue Button "Connector" web site.
---

## API
The Connector provides a simple public HTTP API. Check out the [API documentation](http://api.bluebuttonconnector.healthit.gov) and leave your suggestions and bug reports here on Github.


## Technical architecture
The website is built using the API and some Node.js-based tools, backed by the API. To reduce the cost of maintenance and increase reliability, as of this writing the site is generated as a set of static files and uses free or low-cost hosting systems.


### Updating the data
Currently there is no publicly-writable API. Corrections and additions are handle via two public web forms. Each entry is staged until an admin approves (or rejects) it.

### Building the site
A Grunt.js script handles building many of the files; CSS from Stylus, HTML from Jade, uglifying the JavaScript. The organization directory and profile pages are built by running `npm run build-organizations`. Likewise the app (a.k.a "receivers") directory is built with `npm run build-apps`. Note that these steps require data from the API during the build.

### Deploying
Running `grunt dist` will create a set of deployable files in the `public` directory, which are then copied to `../gh-pages`. It is assumed that a directory by that name will be there, which should be a clone of this repository set to the `gh-pages` branch. `git push origin gh-pages` will then deploy the site to Github pages.
