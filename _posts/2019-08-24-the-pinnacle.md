---
layout: post
title: GSoC 2019-The Pinnacle
excerpt: Often we run into scenarios where it becomes hard to properly save or reproduce results when working with datasets.....
---

Often we run into scenarios where it becomes hard to properly save or reproduce results when working with datasets. The main issue we face is that the dataset gets changed or updated and doesn't run with our existing code or produces same results. For eg.:

* `X` used an online dataset for his college project. He submitted the project that contained the link to the dataset to his teacher. Unfortunately, when the teacher ran the project the online version of the dataset had already been updated with the addition of a new column. His code was unable to handle this new column and failed to run. The teacher gave him a bad grade.
* `Y` wanted to save his research work at various stages with different versions of the same dataset. For this, he had to create directories manually to store the datasets that made it difficult to manage the different versions and wasted a lot of his research time.
* `Z` wanted to store the dataset he used with his project in an online repository.

...and many more.

Well, the following scenarios are now solved if you use `Data Retriever` as the dataset manager for your project. Now, `Data Retriever` not only helps you in cleaning and installing datasets but also in storing dataset in its current state and gives you the ability to share the saved states with others in form of compressed archive.

Here's a look at all the functionalities that I have added to [Data Retriever](https://github.com/weecology/retriever).

The command to commit dataset to a compressed archive by using retriever:

```bash
retriever commit dataset-name -m "commit message" -p path_to_store_archive_file
```

The command to store all your committed datasets in a directory of your choice i.e. in the provenance directory by setting an environment variable `PROVENANCE_DIR`:

```bash
retriever commit dataset-name -m "commit message"
```

The command to see the log of committed datasets stored in provenance directory:

```bash
retriever log dataset-name
```

The command to install committed datasets using a committed archive file.

```bash
retriever install engine-name path_to_archive_file
```

The command to install datasets stored in provenance directory:

```bash
retriever install engine-name dataset-name --hash-value hash
```

For all the above commands corresponding `python interface` is also available.

In future, I would like to extend provenance features to the `Data Retriever` packages for `R` and `Julia`. Also, I would like to add more tests for `Retriever Provenance`. It was my second GSoC working with the awesome folks at [Weecology](https://www.weecology.org). Thanks to the timely inputs from my mentors [Ethan White](https://www.weecology.org/people/ethan-white/) and [Andrew Zhang](https://www.weecology.org/people/andrew-zhang/) at various stages that helped in making the project possible from design to implementation and special thanks to my mentor [Henry Senyondo](https://www.weecology.org/people/henry-senyondo/) for his constant support and guidance in the last one and a half year. It's kind of funny but after working on two GSoC projects I feel emotionally attached to `Data Retriever`.

Here's a list of all the [pull requests](https://github.com/weecology/retriever/pulls?q=is%3Apr+author%3Aapoorvaeternity+is%3Aclosed+created%3A>2019-05-27+is%3Amerged) merged during the coding period while working on `Retriever Provenance`:
* [#1343](https://github.com/weecology/retriever/pull/1343) Add raw data for sample-dataset
* [#1346](https://github.com/weecology/retriever/pull/1346) Add functions for committing dataset
* [#1356](https://github.com/weecology/retriever/pull/1356) Install committed datasets
* [#1360](https://github.com/weecology/retriever/pull/1360) Store committed data in provenance directory if path is not given
* [#1369](https://github.com/weecology/retriever/pull/1369) Show logs of committed datasets in provenance directory
* [#1370](https://github.com/weecology/retriever/pull/1370) Add installation of committed datasets stored in provenance directory
* [#1371](https://github.com/weecology/retriever/pull/1371) Allow installation of committed dataset with python script
* [#1375](https://github.com/weecology/retriever/pull/1375) Add readme for provenance features
* [#1377](https://github.com/weecology/retriever/pull/1377) Refactor code for provenance features
* [#1379](https://github.com/weecology/retriever/pull/1379) Don't use nargs in opts

All of this work was merged to the `master` branch in pull request [#1381](https://github.com/weecology/retriever/pull/1381).

Also, made some commits to [retriever-recipes](https://github.com/weecology/retriever-recipes) a new project created by my fellow GSoC'19 participant [Harshit Bansal](https://www.weecology.org/people/harshit-bansal/) that moved all the retriever dataset scripts to a separate repository for easy maintenenace.

**[Commits on retriever-recipes](https://github.com/weecology/retriever-recipes/commits?author=apoorvaeternity)**

See you guys later!!!
