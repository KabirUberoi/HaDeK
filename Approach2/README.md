# Per Sentence, Subject Based Link forming approach

## Features 

1. Links are being formed between the subject of each sentence and all other entities in that sentence

2. Scoring is done as the fraction of links that are present in wikidata/total links in each sentence individually. If no links can be formed in a sentence, the sentence is ignored for scoring

3. Special characters except . , " ' - are removed only 

4. Confidence score is increased from 0.35 to 0.5 

5. For testing, Only testcases where the score for the ground truth is > 0.1 is considered. This is done so that we can only test cases when the subject is being correctly identified and linked to the correct resl world person.

6. The sentences are being pre-processed such that we make sure each new sentence is in a new line and has a '.' at the end to increase accuracy.

## Main Problems - 

1. Subject not being extracted from text because of being too rare

Eg - In the Passage- 

Richard Keith Mahler (August 5, 1953 in Austin, Texas - March 2, 2005 in Jupiter, Florida) was a starting pitcher in Major League Baseball who played for the Atlanta Braves (1979-1988, 1991), Cincinnati Reds (1989-1990) and Montreal Expos (1991).

The subject is being linked to ""

2. No Direct Link to the given entity existing even tho the entity is highly corelated to the subject 

Eg - ["John_Russell_Reynolds" and "Neurology"] is a link being formed by the system. There exist no direct link between him and "Neurology" hence this links is being given a score of 0 but there does exists a link between him and "Neurologist". 

## Scoring 

Accurate Sentence: 0.54
Minor Inaccurate Sentences: 0.39
Major Inaccurate Sentences: 0.28

On 846 Testcases - (590 - 141 - 115)