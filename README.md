# CAP examples

A repository of examples of what can be done with Caselaw Access Project data.
- [CAP Github repo](https://github.com/harvard-lil/capstone)
- [CAP homepage](https://case.law/)

## Table of Contents
- [Examples](#examples)
- [Contributing instructions](#interested-in-contributing-your-own-examples)
- [Download bulk data](#downloading-bulk-data)
- [Using the API](#using-the-api)
- [Installation Instructions](#install) - install this repo to run examples on your own machine

## Examples
- [Bulk Case Extract](bulk_extract/extract_cases.ipynb) - Get cases from our api's /bulk endpoint. Extract cases into a dataframe.
- [Full Text Search](full_text_search/full_text_search.ipynb) - Get all cases that include a keyword.
- [Full Text Search with Context](api_text_search/api_text_search.py) - Like full text search, only this time using your API key to get the context around the word.
- [Ngrams](ngrams/ngrams.ipynb) – Use the open Arkansas bulk cases to explore interesting words.
- [Bulk Exploration: ngrams and Justice Cartwright](bulk_exploration/cartwright.ipynb) – Use the open Illinois bulk cases to explore interesting words, and look at a Judge's opinion publishing history.
- [Map Courts](map_courts/map_courts.ipynb) - Map all the courts on a U.S. map.
- [Get Judges](get_judges/get_judges.ipynb) - Get judges and return [CourtListener Person urls](https://www.courtlistener.com/api/rest/v3/people/?name_last=Pregerson&name_first=Harry)
- [API to CSV](api_to_csv/api_to_csv.py) - Command line Python3 script with no external dependencies, fetching search results from the cases endpoint and writing to a CSV.
- [Labelling case parties and summarizing cases](labelling_summarizing/labelling_summarizing.ipynb) - Using some basic machine learning to label who the parties in each case were, and then summarizing the case text.

## Interested in contributing your own examples?
1. Fork this repository
2. Add your work
3. Make sure to add any requirements your project needs to [requirements.in](requirements.in)
4. Run ```pip-compile --output-file requirements.txt requirements.in```
5. Add a link in the [Examples section](#examples)
6. Create a [pull request](https://github.com/harvard-lil/cap-examples/compare)
7. Receive gratitude (thank you so much!!)

## Downloading bulk data

#### Helper methods to download whitelisted bulk data
Download the Illinois dataset
```
(capexamples) $ fab get_cases_from_bulk:Illinois
```

Or, download the Arkansas dataset
```
(capexamples) $ fab get_cases_from_bulk:Arkansas
```

Download a dataset with casebody format as xml
```
(capexamples) $ fab get_cases_from_bulk:Illinois,data_format=xml
```


## Using the API
[Read our API documentation.](https://case.law/api/)

In order to download [non-whitelisted](https://case.law/api/#limits) cases, you must [register for an API key](https://case.law/user/register/).

Once you have your API key, copy and paste it into your secret keys file [settings.py](config/settings.py).


## Install
`3.5.4` is the python version we're currently using on CAP, so to keep things simple, we'll be using the same version for these examples.

We recommend installing pyenv — [follow instructions to install here](https://github.com/pyenv/pyenv).

Install your python version using pyenv and activate your virtual environment:
```
$ pyenv install 3.5.4
$ pyenv virtualenv 3.5.4 capexamples
$ pyenv activate capexamples
(capexamples) $
```

Set up!
```
(capexamples) $ pip install -r requirements.txt
(capexamples) $ fab setup
```

To run jupyter notebook examples (i.e. any file ending in .ipynb):
```
(capexamples) $ jupyter notebook
```
