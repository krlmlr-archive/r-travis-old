R-travis
========

Two tiny scripts that faciliate testing R packages with Travis CI.
To test each commit and pull request against stable *and* development versions
of R:

- add the following
[`.travis.yml`](https://github.com/krlmlr/R-travis/blob/master/misc/.travis.yml)
file to the root of your R package on GitHub
- don't forget to add `.travis.yml` to `.Rbuildignore`

```
language: c

env:
  global:
    - RTRAVISPATH=~root/R-travis
    - RTRAVISR="" # add custom R code to be executed before installing package
  matrix:
    - RTRAVISTYPE=quick
    - RTRAVISTYPE=full

# install dependencies
install:
  - sudo git clone https://github.com/krlmlr/R-travis.git $RTRAVISPATH
  - sudo -E $RTRAVISPATH/r-travis install

# run tests
script:
  - $RTRAVISPATH/r-travis test
```
