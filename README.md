R-travis
========

A script that faciliates testing R packages with Travis CI.
To test each commit and pull request:

- add the following
[`.travis.yml`](https://github.com/krlmlr/R-travis/blob/master/misc/.travis.yml)
file to the root of your R package on GitHub
- modify as necessary
- don't forget to add `.travis.yml` to `.Rbuildignore`
- [turn on travis](https://travis-ci.org/profile) for your project

```
language: c

env:
  global:
    - RTRAVISPATH=$HOME/r-travis
    - RTRAVISR="" # add custom R code to be executed before installing package
  matrix:
    - RTRAVISTYPE=quick
    - RTRAVISTYPE=full

# install dependencies
install:
  - curl -L https://raw.github.com/krlmlr/R-travis/master/r-travis -o $RTRAVISPATH
  - chmod +x $RTRAVISPATH
  - sudo -E $RTRAVISPATH/r-travis install

# run tests
script:
  - $RTRAVISPATH/r-travis test
```

Two test environments are run:

- A quick check against current R, without building vignettes or the manual
- A full check against stable *and* development versions of R
