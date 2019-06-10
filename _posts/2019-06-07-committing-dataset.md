---
layout: post
title: GSoC 2019-Committing dataset using Data Retriever
excerpt: The first two weeks of coding period are over....
---

Hello people,

The first two weeks of the coding period are over. Here's a peek into what I have done in the past two weeks.

The first two weeks of my proposal comprised of creating functions for compressing datasets but I have been able to go ahead and implement the first command 
```bash
retriever commit abalone-age -m "commit message" -p path_to_store_archive_file
```
This command creates a compressed file that contains the raw data of the dataset, the dataset script file and a metadata file that contains information about the commit. So basically, it contains every information of a dataset. The `zipfile` module made this task a lot easier.
The compressed file after committing a dataset looks like this:
![zip file]({{site.url}}/assets/image/zip_file.png)

My [PR](https://github.com/weecology/retriever/pull/1338) for this work is still under review and tests and will get merged soon.


In further work, I am going to create functions to extract data from the compressed file and use it for installing the dataset.
