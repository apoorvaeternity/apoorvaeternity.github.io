---
layout: post
title: GSoC 2019-Storing committed datasets in provenance directory
excerpt: We are done with 2/3 of GSoC 2019
---

Hey folks, <br>
We are done with 2/3 of GSoC 2019. The time surely flies.

For the last two weeks, I worked on the reviews on my PR for installation of datasets, added test for it.
I also worked on implementing the command 
```bash
retriever commit abalone-age -m "First commit"
```
In this case, the committed dataset will get stored in the provenance directory which can be set using the environment variable `PROVENANCE_DIR`. 
The provenance directory will store all the committed datasets in case the user does not provide a custom path for storing the dataset.


A log of all the committed datasets will also be maintained inside the provenance directory which can be accessed using the command:
```bash
retriever log dataset_name
```
It will show all the commits for a particular dataset in the following form:
```bash
retriever log abalone-age

Commit: Required results produced with updates
Hash: 78b2ec4a.........
Date: Sun Mar 24 21:45:21 2019 +0530

Commit: Required results produced 
Hash: 4ab32123.........
Date: Sun Mar 24 21:42:11 2019 +0530
```

I will work on implementing this command now.
