<!-- README.md is generated from README.Rmd. Please edit that file -->

# shinycoreci

<!-- badges: start -->

[![Lifecycle Experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
[![R CMD check](https://github.com/rstudio/shinycoreci/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/rstudio/shinycoreci/actions/workflows/R-CMD-check.yaml)
[![Warm library cache](https://github.com/rstudio/shinycoreci/actions/workflows/apps-cache-matrix.yml/badge.svg)](https://github.com/rstudio/shinycoreci/actions/workflows/apps-cache-matrix.yml)
[![Test](https://github.com/rstudio/shinycoreci/actions/workflows/apps-test-matrix.yml/badge.svg)](https://github.com/rstudio/shinycoreci/actions/workflows/apps-test-matrix.yml)
[![Deploy](https://github.com/rstudio/shinycoreci/actions/workflows/apps-deploy.yml/badge.svg)](https://github.com/rstudio/shinycoreci/actions/workflows/apps-deploy.yml)
[![Docker](https://github.com/rstudio/shinycoreci/actions/workflows/apps-docker.yml/badge.svg)](https://github.com/rstudio/shinycoreci/actions/workflows/apps-docker.yml)
[![Dependencies](https://github.com/rstudio/shinycoreci/actions/workflows/apps-deps.yml/badge.svg)](https://github.com/rstudio/shinycoreci/actions/workflows/apps-deps.yml)
<!-- badges: end -->

<!-- This is an R package to install all dependencies to test the bleeding edge of all relevant packages to the Shiny team. -->

<!-- For more direct usage examples, see [`rstudio/shinycoreci-apps`](https://github.com/rstudio/shinycoreci-apps). -->

## Installation

Install the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("pak", repos = sprintf("https://r-lib.github.io/p/pak/stable/%s/%s/%s", .Platform$pkgType, R.Version()$os, R.Version()$arch))
pak::pkg_install("rstudio/shinycoreci")
```

These GitHub packages will be installed to make sure the latest package development is working as expected:

  - [r-lib/cachem](http://github.com/r-lib/cachem)
  - [r-lib/fastmap](http://github.com/r-lib/fastmap)
  - [r-lib/later](http://github.com/r-lib/later)
  - [rstudio/bslib](http://github.com/rstudio/bslib)
  - [rstudio/crosstalk](http://github.com/rstudio/crosstalk)
  - [rstudio/DT](http://github.com/rstudio/DT)
  - [rstudio/dygraphs](http://github.com/rstudio/dygraphs)
  - [rstudio/flexdashboard](http://github.com/rstudio/flexdashboard)
  - [rstudio/fontawesome](http://github.com/rstudio/fontawesome)
  - [rstudio/htmltools](http://github.com/rstudio/htmltools)
  - [rstudio/httpuv](http://github.com/rstudio/httpuv)
  - [rstudio/pool](http://github.com/rstudio/pool)
  - [rstudio/promises](http://github.com/rstudio/promises)
  - [rstudio/reactlog](http://github.com/rstudio/reactlog)
  - [rstudio/rsconnect](http://github.com/rstudio/rsconnect)
  - [rstudio/sass](http://github.com/rstudio/sass)
  - [rstudio/shiny](http://github.com/rstudio/shiny)
  - [rstudio/shinymeta](http://github.com/rstudio/shinymeta)
  - [rstudio/shinytest](http://github.com/rstudio/shinytest)
  - [rstudio/shinytest2](http://github.com/rstudio/shinytest2)
  - [rstudio/shinythemes](http://github.com/rstudio/shinythemes)
  - [rstudio/shinyvalidate](http://github.com/rstudio/shinyvalidate)
  - [rstudio/thematic](http://github.com/rstudio/thematic)
  - [rstudio/webdriver](http://github.com/rstudio/webdriver)
  - [rstudio/websocket](http://github.com/rstudio/websocket)
  - [schloerke/shinyjster](http://github.com/schloerke/shinyjster)

Tools for manual and automated testing of shiny apps.

## Running manual tests

First, clone the shinycoreci-apps repo. Next, install [`remotes::install_github("rstudio/shinycoreci")`](https://github.com/rstudio/shinycoreci). You may need to add your `GITHUB_PAT` to your R Environ file (See `?usethis::edit_r_environ` and `?usethis::browse_github_pat`)

  - [RStudio IDE](https://rstudio.com/products/rstudio/download/#download) - `shinycoreci::test_in_ide()`
  - [RStudio Cloud](http://rstudio.cloud) - `shinycoreci::test_in_ide()`
  - [RStudio Server Pro](https://colorado.rstudio.com) - `shinycoreci::test_in_ide()`
  - R Terminal / R GUI - `shinycoreci::test_in_browser()`
  - (Any) Web Browser - `shinycoreci::test_in_browser()`
  - [shinyapps.io](http://shinyapps.io) - `shinycoreci::test_in_shinyappsio()`
  - [RStudio Connect](http://beta.rstudioconnect.com) - `shinycoreci::test_in_connect()`
  - SSO - `shinycoreci::test_in_sso(release = "focal")`
    \> will require docker login. Run `docker login` in the terminal
  - SSP - `shinycoreci::test_in_ssp(release = "centos7")`
    \> will require docker login. Run `docker login` in the terminal

All testing functions may be run from within the IDE (except for R Terminal / R GUI).

#### IDE Example

``` r
# install.packages("pak", repos = sprintf("https://r-lib.github.io/p/pak/stable/%s/%s/%s", .Platform$pkgType, R.Version()$os, R.Version()$arch))

# Install the latest from pak
pak::pkg_install("rstudio/shinycoreci")
# Install shinyverse
# Run all manual tests
shinycoreci::test_in_ide()
```

<!--
## View and manage automated test results

To view and manage test results, first make sure your working directory is the `shinycoreci-apps` repo.

Use `shinycoreci::view_test_results()` to obtain an overview of the most recent test runs (it should prompt a **shiny** app that looks similar to this):

<div align="center">
  <img src="README_files/view-test-results.png" />
</div>

If you see failures that indicate a difference in **shinytest2** baselines (as above), you may need to just view and approve the differences.

To obtain and correct the shinytest differences, use `shinycoreci::fix_all_gha_branches()`. This function will walk you through the steps needed to update all `shinytest` failures and merge in the latest information from each `gha-` branch.  To approve the differences, click on the "Update & click" button. To reject the differences, click on "Quit" button.

If you receive the error `No information found for sha: ABC1234 . Do you have a valid sha?`, you may have to provide the git sha value directly: `shinycoreci::fix_all_gha_branches(sha = "XYZ5678")`.

In the event that all testing failures can not be addressed by updating shinytest baselines, have a look at the [GHA actions](https://github.com/rstudio/shinycoreci-apps/actions) build log and keep the following troubleshooting tips in mind:
-->

### Troubleshooting test failures

1.  Failures on old versions of R

If a testing app passes on recent version(s) of R, but fails in a suprising way on old R version(s), it may be due to an old R package version. In that case, modify the tests to run only if a sufficient version of the relevant package is available ([for example](https://github.com/rstudio/shinycoreci-apps/blob/5691d1f4/apps/145-dt-replacedata/tests/shinytest.R)).

2.  Other failures that can’t replicated locally

Other surprising failures are often the result of timing issues (which can be difficult, if not impossible, to replicate locally). If your testing app uses dynamic UI and/or doesn’t have proper input/output bindings, **shinytest** probably needs to know how long to wait for value(s) to update (in this case, use `waitForValue()`, [for example](https://github.com/rstudio/shinycoreci-apps/blob/5691d1f4/apps/021-selectize-plot/tests/shinytest/mytest.R#L10-L11)). Somewhat similarly, when checking DOM values with **shinyjster**, you may need to wait for an update to DOM element(s) before checking value(s), in which case you can write a recursive function that keeps calling itself until the DOM is ready ([for example](https://github.com/rstudio/shinycoreci-apps/blob/5691d1f4/apps/187-navbar-collapse/app.R#L24-L34)).

3.  All of the windows shinytest plots have failed

When Windows virtual images update on GitHub Actions, the graphics device may behave exactly as the prior graphics device. Check to see if your windows `Image Version` has updated. (To view this, inspect the top lines in `./apps/sys-info-win-XX.txt` for a change.) You should accept the updated shinytest output for the build with the higher `Image Version`.

## Contribute a testing app

When contributing a testing app, try to do the following:

  - Capture all the functionality with automated tests.
      - Also, where possible, write “light-weight” tests (that is, try and avoid **shinytest2** `$expect_screenshot()` where possible since they are prone to false positive differences and thus have a maintenance cost).
      - If the app does need manual testing, flag the testing app for manual testing with `shinycoreci::use_manual_app()`.
  - Add a description to the app’s UI that makes it clear what the app is testing for.

Note that **shinycoreci** only supports `{testthat}` testing framework. Call `shinytest2::use_shinytest2(APP_DIR)` to use `{shinytest2}` and `{testthat}`

1.  **shinytest**: primarily useful for taking screenshots of shiny output binding(s) (before or after interacting with **shiny** input bindings). [See here](https://github.com/rstudio/shinycoreci-apps/blob/5691d1f/apps/001-hello/tests/shinytest/mytest.R) for an example (note that `shinytest::recordTest()` can be used to generate shinytest testing scripts).

2.  **shinyjster**: primarily useful for asserting certain expectations about the DOM (in JavaScript). [See here](https://github.com/rstudio/shinycoreci-apps/blob/5691d1f/apps/001-hello/app.R#L37-L61) for an example (note that `shinyjster::shinyjster_js()` needs to be placed in the UI and `shinyjster::shinyjster_server(input, output)` needs to be placed in the server).

3.  **testthat**: primarily useful in combination with `shiny::testServer()` to test server-side reactive logic of the application.

<!-- end list -->

  - [See here](https://github.com/rstudio/shinycoreci-apps/blob/5691d1f4/apps/001-hello/tests/testthat/tests.R#L4) for an example.
  - Call `shinycoreci::use_tests_testthat(app_dir)` to provide the file scaffolding necessary to run the **testthat** tests

## Pruning old git branches

To help us store and manage the test results, git branches are automatically created for each test run. These branches are automatically removed on GitHub after 1 week of no activity, but you may want to periodically remove them on your local machine as well:

``` bash
git fetch --prune
```

## What workflows are available?

This repo contains several [GitHub Actions](https://github.com/features/actions) workflows:

  - [**runTests:**](https://github.com/rstudio/shinycoreci-apps/actions?query=workflow%3ArunTests) Run the automated tests (via `shiny::runTests()`).
  - [**Docker:**](https://github.com/rstudio/shinycoreci-apps/actions?query=workflow%3ADocker) Create all SSO and SSP docker images
  - [**Deploy**](https://github.com/rstudio/shinycoreci-apps/actions?query=workflow%3ADeploy): Deploy all testing apps to [shinyapps.io](shinyapps.io) and [beta.rstudioconnect.com](https://beta.rstudioconnect.com)

The **runTests** workflow runs automatically on every code change to `shinycoreci-apps` as well as every night (around midnight UTC). The other workflows may be triggered via `shinycoreci::trigger_docker()` and `shinycoreci::trigger_deploy()`

<!--
### Managing R package dependencies

"Core" `shinycoreci-apps` R package dependencies come from **shinycoreci**'s [DESCRIPTION file](https://github.com/rstudio/shinycoreci/blob/master/DESCRIPTION); and so, that file may be modified to test different versions of different packages in the shinyverse.

Application-specific R package dependencies are automatically inferred (and installed at run-time) using `renv::dependencies()`.

> Note: `renv::dependencies()` are taken from CRAN, not GitHub Remotes.
 -->

## FAQ:

If you run into an odd `{pak}` installation issue:

  - Run `pak::cache_clean()` to clear the cache and try your original command again
