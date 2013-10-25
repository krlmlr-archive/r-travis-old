R-travis
========

Two tiny scripts that faciliate testing R packages with Travis CI.
To test each commit and pull request against stable *and* development versions
of R:

- add the following
[`.travis.yml`](https://github.com/krlmlr/R-travis/blob/master/misc/.travis.yml)
file to the root of your R package on GitHub
- modify as necessary
- don't forget to add `.travis.yml` to `.Rbuildignore`
- [turn on travis](https://travis-ci.org/profile) for your project

```
