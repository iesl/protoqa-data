# Data Format
All files are in `jsonl` format. Below we describe the format expected of each line.

## Answer Cluster Data

```
{
  "metadata": {
    "id": <str> unique id of this question,
    "source": <str> source of answer strings (eg. "umass-crowdsource", url, etc.)
  },
  "question": {
    "original": <str> original string form of this question,
    "normalized": <str> cleaned form of question suggested for model input
  },
  "answers": { <dict[str,int]> dictionary from answers to their counts, eg.
    "raw": { <dict[str,int]> answer strings to counts, eg.
        "answer_one": 4,
        "answer_two": 7,
        ...
      },
    "clusters": {dictionary from unique cluster ids to cluster information, eg.
      "r#q#.1": {
        "count": <int> number of answers which correspond to this cluster,
        "answers": <list[str]> list of answers which correspond to this cluster,
      },
      ...
    }
  "num": {
    "answers": <int> sum of answer points,
    "clusters": <int> number of clusters,
  },
}
```

### Crowdsourced Data
The "raw" answers went through additional manual cleaning (eg. filtering out nonsense answers, spell correction), and therefore the answers in "raw" and "clusters" may be different.

### Scraped Data
There is only one string available per cluster. In particular, the scraped dev set is not intended for use with the generative evaluation, as the performance will be quite poor.

## Assessment Data

```
{
  "question_id": <str> unique id of the associated question,
  "assessments": { <dict[str,str]> association from answer strings to cluster ids, eg:
    "answer_one": "r#q#.0",
    "answer_two": "r#q#.4",
    ...
  }
}
```
