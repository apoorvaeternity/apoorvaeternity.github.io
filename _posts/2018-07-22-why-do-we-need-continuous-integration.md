---
layout: post
title: GSoC 2018-Why do we need continuous integration?
excerpt: When software is built traditionally the integration process....
---

When software is built traditionally the integration process takes place at the end when everyone working on the software has completed their part(module) of the software. This makes integration very difficult and takes a lot of time(weeks or even months). In continuous integration building, testing and integration of code happen more regularly than in the traditional way.

So, what really is continuous integration? Suppose there are two developers, one of the developers writes code on his laptop at home and another developer writes code on his desktop in the office for the same software product and they integrate their changes together in a place called the source repository. They then build the combined software from the pieces of code they each wrote and test that it works the way they expected on a continuous integration server. This is known as continuous integration.

There are several continuous integration services available for GitHub such as Travis CI, AppVeyor, CircleCI etc.
It is a good practice to use continuous integration when working in teams and even when working alone. It also helps on platforms such as GitHub in knowing whether a patch that has been made in the form of a pull request or commit is working perfectly or not against the written tests. One can also configure the environments for continuous integration for eg. Travis CI uses a `travis.yml` file to know the configurations for a project.
The `travis.yml` file for `retrieverdash` looks like this.
```yaml
language: python
python:
  - 3.5

env:
  - DJANGO=2.0

addons:
  postgresql: "9.4"
  apt:
    sources:
      - travis-ci/sqlite3
    packages:
      - sqlite3
services:
  - postgresql

install:
  - pip install -r retrieverdash/requirements.txt
script:
  - python retrieverdash/setup.py install
  - retriever ls
  - pytest -v
  - python retrieverdash/manage.py test 
before_script:
  - sqlite3 --version
  - psql -c 'create database testdb;' -U postgres
```

Getting back to my GSoC project, I have cleared my second evaluation :)<br>
The project is in its final phase. We have the dashboard and the script in place. Right now the major thing I have to add is support for spatial datasets.<br>
See you next time.

