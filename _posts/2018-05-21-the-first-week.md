---
layout: post
title: GSoC 2018-The First Week of Coding Period
excerpt: Hey folks of planet Earth(I hope aliens read it someday), The first week of the coding period has.... 
---

Hey folks of planet Earth(I hope aliens read it someday),<br>
The first week of the coding period has passed.<br>
I have been a bit slow because of my University Exams but surely I will cover up any lost or lag in my work in the coming weeks.
<br><br>
Though I was able to get only one [pull request](https://github.com/weecology/retrieverdash/pull/5) merged in the first week on the [Retriever Dashboard](https://github.com/weecology/retrieverdash/) repository, it is a major one.<br><br>
I have added a file `status_dashboard_tools.py`. This file contains the functions that will be required to check the installation of datasets.
<br><br>
Some of the functions I have added are:<br>
`get_dataset_md5`- This function finds the md5 value of a dataset. What we are actually doing is converting the datasets to csv files and then we find the md5 value of those files collectively. Since the md5 value is unique we use it to find whether there was any change in the dataset by comparing it with previous values. So it is one of the important functions.
<br>
`create_dirs`- This function creates the directories required for keeping the files for generating the diff.
<br>
`dataset_to_csv`-This function converts the tables of a dataset to csv file.
<br>
`diff_generator`- This function generates the `diff` of the datasets if there are changes by comparing the csv files in the `old` and `current` directory created by `create_dirs` function and keeps them in the `diff` directory.
<br><br>
So `status_dashboard_tools.py` just contains a few major functions. Now I am working on the second script `dashboard_script.py`. It will be used for checking the installation of datasets by using functions in `status_dashboard_tools.py` and creating a log file. This script will be run at regular intervals using `cron`.
The best part is that it will check multiple datasets parallelly :).
<br><br>
The first week was awesome. More awesomeness is coming soon. Stay tuned.

