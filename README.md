# Drake DataSync
Push a CSV file to a Socrata dataset using [Drake](https://github.com/factual/drake) and [DataSync](http://socrata.github.io/datasync/)

This project provides a data workflow that:
1. Reads a CSV file
2. Creates Socrata-friendly field names using [slugify-headers](https://github.com/timwis/slugify-headers)
3. Pushes to a Socrata data store using the efficient data transport ([DataSync](http://socrata.github.io/datasync/))

By using [Drake](https://github.com/factual/drake) it creates an extensible workflow (or the beginnings of one, at least)
rather than procedural, one-off code.

## Requirements
- Java Runtime (for DataSync and Drake)
- [Drake](https://github.com/Factual/drake)
- [DataSync](https://socrata.github.io/datasync/)
- Python (for slugify-headers)
- [jq](https://stedolan.github.io/jq/)

## Usage
Copy `config.sample.json` to `config.json` and fill in its values. Generate a Socrata token [here](https://dev.socrata.com/register).
Then execute the following command inside the project folder, replacing `INFILE` and `DATASET` values with the path to the dataset
and the Socrata dataset ID, respectively.
```bash
$ drake --vars="INFILE=path/to/data.csv,DATASET=abcd-1234"
```
Note: I'm new to python so `slugify-headers` may not be as easy to install as it could be. For now, you need to install its
dependencies in order for this workflow to utilize it. This can be done using `pip install -r requirements.txt` inside its folder.

## Roadmap
Given a config file of table names and Socrata dataset IDs, extract each table from a database and push it to its corresponding
Socrata dataset.