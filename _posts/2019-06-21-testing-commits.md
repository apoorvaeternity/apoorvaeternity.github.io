---
layout: post
title: GSoC 2019-Testing dataset committed using Data Retriever
excerpt: The 3rd and 4th week of the coding period were spent mostly in testing and improving
---

The 3rd and 4th week of the coding period was spent mostly in testing and improving the work that I had done in the first two weeks.

In the first two weeks of the coding period, I enhanced retriever to make it possible to commit datasets. After the functionality was added it was time for testing. So I wrote the test case for it.

The test case used a scenario-based testing approach:

For this, I added a new sample dataset named `dataset-provenance` for testing. I installed the dataset and committed it using retriever and then I changed the source of raw data for the dataset and the committed dataset again in a temporary directory. The zipped file that is created after a dataset is committed has a hash value which is a combination of the md5 values of raw data and script of the dataset.
The expected file names of the committed datasets were already known and it was then checked whether the files are in the temporary directory or not. If the files are there then the commit has been made successfully while considering the changes in raw data.

Pytest makes it easier to pass the expected values(a list of tuples) to a test case. Just like a loop, it can run the test case for multiple expected values. 
```python
test_commit_details = [
    (
        "dataset_provenance",
        {
            "main": MASTER_BRANCH
            + "test/raw_data/dataset-provenance/modified/dataset_provenance.csv"
        },
        {
            "original": "dataset-provenance-c147c9.zip",
            "modified": "dataset-provenance-6ca7c9.zip",
        },
    )
]

@pytest.mark.parametrize(
    "script_file_name, modified_table_urls, expected_archives", test_commit_details
)
def test_commit(script_file_name, modified_table_urls, expected_archives):
    test_dir = mkdtemp(dir=os.path.dirname(os.path.realpath(__file__)))
    os.chdir(test_dir)
    script_path = os.path.join(file_location,"raw_data/scripts/", script_file_name)
    script_module = get_script_module(script_path)
    script_json = "{}.json".format(script_path)
    setattr(script_module, "_file", script_json)
    setattr(script_module, "_name", script_file_name.replace("_", "-"))
    # install original version
    install_and_commit(script_module, test_dir=test_dir, commit_message="Original")
    # install modified version
    install_and_commit(
        script_module,
        test_dir=test_dir,
        commit_message="Modified",
        modified_table_urls=modified_table_urls,
    )
    # check if the required archive files exist
    original_archive_path = os.path.join(test_dir, expected_archives["original"])
    original_archive_exist = os.path.isfile(original_archive_path)
    modified_archive_path = os.path.join(test_dir, expected_archives["modified"])
    modified_archive_exist = os.path.isfile(modified_archive_path)
    os.chdir(file_location)
    rmtree(test_dir)

    assert original_archive_exist == True
    assert modified_archive_exist == True

```

The code for the test case is quite self-explanatory. Here I am checking whether the expected zipped files are there or not after the commit is made.
All of this work has already been merged and my next goal is to allow installation of the committed datasets using Data Retriever. 
