R-travis
========

Two tiny scripts that faciliate testing R packages with Travis CI.
Add the following `.travis.yml` file to the root of your R package on GitHub
to test each commit and pull request against stable *and* development versions
of R:

```
# it is not really python, but there is no R support on Travis CI yet
language: python

# install dependencies
install:
  - sudo git clone https://github.com/krlmlr/R-travis.git ~root/R-travis
  - sudo ~root/R-travis/install

# run tests
script:
  - "for mode in stable devel; do ~root/R-travis/script $mode; done"
```
