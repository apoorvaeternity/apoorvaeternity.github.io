---
layout: post
title: GSoC 2018-Reflections On The First Month
---

The first month of the coding period is almost over.
<br>
In the last two weeks I have worked on the main script `dashboard_script.py` that will be used for checking the installation of datasets. This script makes use of the functions available in `status_dashboard_tools.py` for accomplishing the task of checking datasets.
<br>
This script got merged in pull request [#6](https://github.com/weecology/retrieverdash/pull/6). The script is working perfectly the way we want it to and generates `dataset_details.json` that contains the information regarding a dataset i.e. whether it is installing successfully or not and other details such as `md5`.
This script checks the installation of datasets in parallel.
<br>
Right now we are dealing with a problem of SQLite databases locking when using the `SQLite engine`. We are creating a new database for each dataset every time so there should be no issue of concurrency but still, the issue occurs. We are working on that.
The script works well with the `CSV engine`.
<br>
<br>
I have made a pull request(to be merged) [#10](https://github.com/weecology/retrieverdash/pull/10) that adds the test for the dashboard. Basically, it creates a scenario in which a dataset changes. It creates html diff files and csvs in the test and checks whether they exist in respective directories or not.
<br>For this, I have also added a `sample-dataset` in pull request [#11](https://github.com/weecology/retrieverdash/pull/11). In this PR I added two versions of a dataset to perform the testing.
We are using `pytest-django`(pytest-django is a plugin for pytest that provides a set of useful tools for testing Django applications and projects) for performing testing.
<br>
This PR is on the verge of getting merged.
<br>
<br>
I also have set up the cron job locally for the script. I have used `django-crontab` so that cron jobs can be easily added or removed using `manage.py`.
<br>
I will send a PR for adding `cron jobs` after [#10](https://github.com/weecology/retrieverdash/pull/10) gets merged because [#10](https://github.com/weecology/retrieverdash/pull/10) has a few changes that I require.
<br>
<br>
Now I have started my work on the dashboard.
