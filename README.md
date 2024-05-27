# Verifiability-Granular
This dataset was created by processing the data collected by [Liu et al](https://arxiv.org/abs/2304.09848). More details can be found in our ACL 2024 Findings [paper](), titled "Peering into the Mind of Language Models: An Approach for Attribution
in Contextual Question Answering".

## Dataset
The dataset contains 2 jsonl files - dev and test split.
| split | num_statements | num_spans |
|---|---|---|
| Dev | 170             |  272      |
| Test   | 197              | 320       |

Each jsonl file contains the following fields:
| Field Name        | Field Value | Description                                 |
|-------------------|-------------|----------------------------------------------|
| **question** | *String* | This is the question that the LLM needs to answer.      |
| **summary** | *String* | This is the answer from the LLM with annotations. The annotation format is same as in [QuoteSum](https://arxiv.org/abs/2311.04886). Annotated spans are identified by `[ number {text} ]`. The `text` is attributed to passage `number - 1`.  |
| **chunk** | *String* | This is a substring of the summary. It is for this chunk that the annotation is present in summary. | 
| **passages** | *List[String]* | These are the paragraphs that form the context for the question.         |

A sample datapoint with `index=13` from the test split  is:
| Field Name        | Field Value |
|-------------------|-------------|
| **question** | who sings i got a thing for you | 
| **summary** | There are several songs with similar titles. One is by **Jim Bianco** called "I Got a Thing for You". Another song with a similar title is[ 2  "Thing for You" by **David Guetta** and **Martin Solveig**. ] Is one of these what you were looking for? | 
| **chunk** | Another song with a similar title is "Thing for You" by **David Guetta** and **Martin Solveig**. |
| **passage with `index=1`** | " Thing for You " is a song by French DJs David Guetta and Martin Solveig . |
