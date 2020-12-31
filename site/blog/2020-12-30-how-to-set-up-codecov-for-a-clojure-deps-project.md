---
title: How To Set Up Codecov For a Clojure Deps Project
date: 2020-12-30
---

I recently set up code coverage reporting with [Codecov](https://about.codecov.io/product/features/) for a Clojure project of mine that uses tools.deps and builds on CircleCI. It turned out to be pretty easy but the documentation for the various parts was a bit ambiguous, so I wrote down the steps here in case you're looking to do the same. You can see all the changes it took together in context in [this commit](https://github.com/kiramclean/morphy/commit/cd66a0414807ab19d025a2ce0abe7cb66d8f1dde) where I set it up for my project.

## Assumptions

These instructions assume your project uses the same specific set of tools as me:

- Clojure with tools.deps
- Github
- CircleCI
- Codecov

The same idea should work fine with other combinations of services, but you might have to do things slightly differently or tweak some syntax if you use e.g. Gitlab instead of Github or Travis instead of CircleCI.

## 1. Set up the project in Codecov

- Sign in to Codecov with Github
- Click "Add New Repository" on the dashboard for your github user/organization (the url should be something like `https://codecov.io/gh/<gh-username>`)
- Select the repo

This should leave you at a screen that shows you a Codecov token. If not, click on the "Settings" tab for your project in Codecov to see thee token. Copy it.

## 2. Add the Codecov token to CircleCI

- In CircleCI "Project Settings" > "Environment Variables" set `CODECOV_TOKEN` to the value copied from above

I'm assuming your project is already building on CircleCI. If not you can do similar steps to above on Circle (sign in with Github and add your project), and crib my [config for a Clojure deps project](https://github.com/kiramclean/morphy/blob/cd66a0414807ab19d025a2ce0abe7cb66d8f1dde/.circleci/config.yml) to get started.

## 3. Generate Codecov reports from test runs in CI

- Add a new alias to your deps project to run tests and generate the Codecov reports using [cloverage](https://github.com/cloverage/cloverage):

```edn
:coverage {:extra-paths ["test"]
           :extra-deps {cloverage/cloverage {:mvn/version "1.2.1"}}
           :main-opts ["-m" "cloverage.coverage" "-p" "src" "-s" "test" "--codecov"]}
```

- Update your run tests step in your CircleCI config to use this new alias:

```yaml
- run:
    name: Run tests
    command: clojure -M:coverage
```

## 4. Send the coverage reports to Codecov

- Add a step in your CircleCI config to send the reports to Codecov:

```yaml
- run:
    name: Send test coverage to Codecov
    command: bash <(curl -s https://codecov.io/bash)
```


## Caveats

Code coverage isn't a great metric for the quality of your test suite. It's pretty easy to write a couple of tests that exercise most of your code but don't prove much about it's correctness, at least in Clojure where your whole program is basically a pipeline to transform data. I still use this metric though. I find it useful as a high level check to see if there are entirely untested functions, which can also help find dead code. Anyway, just a note of caution to not lean too heavily on code coverage metrics as a measure of the quality of your test suite. It's more like a flag that gets raised if you forget to test something altogether. High code coverage doesn't necessarily indicate a good test suite, but low code coverage definitely indicates a bad one.