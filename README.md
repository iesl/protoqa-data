# protoqa-data


Dataset for ProtoQA	 ("family feud") data.  See [paper](https://arxiv.org/abs/2005.00771) for details.

## General data format:

##### Data Files: 
Each line is a json dictionary, in which:
* **question** contains the question (in original and a normalized form)
* **answerstrings** contains the original answers provided by survey respondents (when available), along with the counts for each string. Because the FamilyFeud data has only cluster names rather than strings, those cluster names are included with 0 weight.
* **answer-clusters** lists clusters, with the count of each cluster and the strings included in that cluster.  Each cluster is given a unique ID that can be linked to in the assessment files. 

##### Assessment files

The file *data/dev/crowdsource_dev.assessments.jsonl* contains mappings from additional human and model answers to clusters, to evaluate different assessment methods. 
* **question**: contains the ID of the question
* **assessments**: maps individual strings to one of three options, either the answer cluster id, "invalid" if the answer is judged to be bad, or "valid_new_cluster" if the answer is valid but does not match any existing clusters. 

##### File organization:

* **data/train/protoqa_train.jsonl**: 8781 instances for training or fine-tuning scraped from Family Feud fan sites (see paper). Scraped data has answer clusters with sizes, but only has a single string per cluster (corresponding to the original cluster name(0
* **data/dev/protoqa_scraped_dev.jsonl**: 979 instances sampled from the same Family Feud data, for use in model validation and development. 
* **data/dev/crowdsource_dev.jsonl**: 51 questions collected with exhaustive answer collection and manual clustering, matching the details of the eval test set (roughly 100 human answers per question)
* **data/dev/crowdsource_dev.assessments.jsonl**: assessment file (format described above) for study of assessment methods. 




* This repository also contains a **data statement** (based on [Datasheets for Datasets (Gebru et al. 2020)](https://arxiv.org/pdf/1803.09010.pdf) and [earlier NLP-specific work(Bender and Friedman 2018)](https://www.aclweb.org/anthology/Q18-1041.pdf)) to provide transparency in data use and encourage others to do so.  This is a preliminary version of the statem	ent; please post issues in the repository or contact the authors if you have questions regarding the data details or suggestions regarding the dataset use. 
