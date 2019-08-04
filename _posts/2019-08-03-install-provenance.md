---
layout: post
title: GSoC 2019-Installing datasets stored in provenance directory
excerpt: Just two more weeks left for the end.....
---
Hey everyone,<br>
Just two more weeks to go for the end of GSoC 2019.
Here's a look into what I did in the past two weeks.

Last two weeks I worked on implementing two things.<br>
Created a command to see the log of datasets stored in the provenance directory.
```bash
retriever log dataset_name
```

For eg.
```bash
retriver log abalone-age

Commit message: New test
Hash: 02ee77
Date: 07/27/2019, 20:30:00

Commit message: save dataset
Hash: a76e77
Date: 07/19/2019, 18:22:31
```
In python interface it can be used like this:
```python
from retriver import commit_log
commit_log('abalone-age')
```

Created a command to install datasets from provenance directory. It's the same as the command used for installing datasets.
The only difference is that if the user provides a hash value with the command for installation of dataset then the installation has to be 
performed by using already committed dataset in the provenance directory.<br>
Here's how to use it:
```bash
retriever install sqlite dataset --hash hash_value
```
For eg.
```bash
retriever install sqlite abalone-age --hash 02ee77
```
In python interface it can be used like this:
```python
from retriever import install_csv
install_csv('abalone-age', hash='02ee77')
```
The pull request for the installlation of dataset from the provenance directory is open and under review.




