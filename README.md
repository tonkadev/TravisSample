[![Build Status](https://travis-ci.org/Krinkle/travis-ci-node-and-browser-qunit.svg?branch=master)](https://travis-ci.org/Krinkle/travis-ci-node-and-browser-qunit)

# Run QUnit tests in NodeJS + WebKit using Travis CI!

This project is a little demonstration of how to approach continuous integration
by running QUnit tests inside a headless browser (phantomjs) and/or inside nodejs
(depending on whether your library is intended for usage in either or both platforms).

Many front-end developers seem to have little exposure to [TDD](https://en.wikipedia.org/wiki/Test-driven_development) and [CI](https://en.wikipedia.org/wiki/Continuous_integration).

# Get started

Clone or fork this repository and be sure to run the following two commands to
install the dependencies:
```bash
git submodule update --init
npm install
```

# Tell me more

There is an awesome project called [Travis CI](http://travis-ci.org/) which is
a cloud-based CI, for open source projects. It is built for GitHub so you can
make a project in GitHub, and hook it up to Travis. Then, whenver you push,
or get a pull-request,  Travis CI will automatically run the tests and report
back on any problems.

This boilerplate repository is also hooked up to Travis ([view build history](http://travis-ci.org/#!/Krinkle/travis-ci-node-and-browser-qunit/builds)).

Just get into it, have a look at it all, you'll get the hang of it, it's easy!
If you've got any problems, feel free to ask on Twitter or [create an issue](https://github.com/keithamus/travis-ci-node-and-browser-qunit/issues).

* [@keithamus](https://github.com/keithamus) ([Twitter](https://twitter.com/keithamus))
* [@Krinkle](https://github.com/Krinkle) ([Twitter](https://twitter.com/TimoTijhof))

By default Travis-CI will execute the `npm test` command, which in this example
repository runs `grunt test` and `node test/node-index.js`. The Gruntfile takes care
of running JSHint and running the QUnit tests in a headless WebKit browser (PhantomJS).
The node script runs the unit tests in node without a browser environment.

Depending on the kind of project you have you may want to keep only one of these.

If your application only runs in a browser:
* Remove ` && node test/node-index.js` from the `scripts.test` property in `package.json`
* Remove `test/node-test.js`
* Remove `grunt` (not `gruntjs`) from the `devDependencies` property in `package.json`

If your app is written specifically for NodeJS (e.g. uses npm packages), then:
* Remove `qunit` from the `initConfig` call in `Gruntfile.js`
* Remove `grunt.loadNpmTasks('grunt-contrib-qunit');` from `Gruntfile.js`
* Remove `grunt-contrib-qunit` from the `devDependencies` property in `package.json`
