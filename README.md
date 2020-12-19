# ProtoQA Dataset

This repository contains the dataset for ProtoQA ("Family Feud").  See [the paper](https://arxiv.org/abs/2005.00771) for details on dataset creation.

## Data Files: 
Each line is a json dictionary, in which:
* **question** contains the question (in original and a normalized form)
* **answers** (where available) contains:
  * **raw** original answers provided by survey respondents (when available) with their counts
  * **clusters** which include the score for each cluster and the strings included in that cluster
  
For a full description of the data format, see [DATAFORMAT.md](DATAFORMAT.md).


## File organization:

* **data/train/train.jsonl**: 8781 instances for training or fine-tuning scraped from Family Feud fan sites (see paper). Scraped data has answer clusters with sizes, but only has a single string per cluster (corresponding to the original cluster name.
* **data/dev/dev.scraped.jsonl**: 979 instances sampled from the same Family Feud data, for use in model validation and development. 
* **data/dev/dev.crowdsourced.jsonl**: 51 questions collected with exhaustive answer collection and manual clustering, matching the details of the eval test set (roughly 100 human answers per question).
* **data/test/test.questions.jsonl** 102 questions for evaluation. (Note that the test set contains questions only.)


## Notes:
This repository contains a [data statement](DATASTATEMENT.md) (based on [Datasheets for Datasets (Gebru et al. 2020)](https://arxiv.org/pdf/1803.09010.pdf) and [earlier NLP-specific work (Bender and Friedman 2018)](https://www.aclweb.org/anthology/Q18-1041.pdf)) to provide transparency in data use and encourage others to do so.  This is a preliminary version of the statement; please post issues in the repository or contact the authors if you have questions regarding the data details or suggestions regarding the dataset use. 
