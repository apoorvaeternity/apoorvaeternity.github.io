---
layout: post
title: GSoC 2019-Installing committed datasets
excerpt: With the end of the 6th week we are now in the mid of GSoC 2019...
---

Hey everyone,

With the end of the 6th week we are now in the mid of GSoC 2019.

Last two weeks I was mostly involved with life but I was able to work on the installation of committed datasets using retriever.
Now it's possible to commit datasets using `retriever` and install the committed dataset back to the database of your choice.
Currently, it is working for only datasets with `JSON` scripts. For supporting datasets with `.py` scripts the scripts will have to be modified because
they override the `download` function to perform extra processing.

I have already opened a [PR](https://github.com/weecology/retriever/pull/1356) for the above work. I am still working on adding the test.

Usage example:
```bash
retriever install sqlite portal-b8b17d.zip
```

```python
from retriever import install_csv
install_csv('portal-b8b17d.zip')
```

As you can see there are no new commands for installation of committed dataset. The user just needs to provide the path to the committed zip file and everything
else remains the same.
After the above work gets merged the major part of the project will be done.
