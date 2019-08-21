# NLP - Natural Lenguage Processing

## Week 1 - Language Terminology + preprocessing techniques
Start before ML: There's a course Speech and Language Proccessing Standford
Watch YouTube Playlist up to 2.5
### State of Language Technology
Mostly solved:
- Spam detection
- Part-of-speech (POS) tagging
- Named entity recognition (NER)
Making good progress:
- Sentiment analysis
- Coreference resolution 
- Word sense disambiguation (WSD) "mouse" PC|animal
- Parsing 
- Machine translation (MT)
- Information Extraction (IE)
Still really hard:
- Question answering (QA)
- Paraphrase
- Summarisation
- Dialog
### In this class
Teaches key theory and methods for statistical NLP:
- Viterbi
- Naïve Bayes, Maxent classifiers
- N-gram language modelling
- Statistical Parsing
- Inverted index, tf-idf, vector models of meaning
For practical, robust real-world applications
- Information extraction
- Spelling correction
- Information retrieval
### Text processing
#### Regular expressions (Most basic)
Most of the time in NLP we try to reduce two kind of errors: 
- False positives (accuracy)
- False negatives (recall)
How to use regex in practical NLP
On particular patterns such as: phone numbers, month abbreviations, state names 
#### Word Tokenisation
Every NLP task needs to do text normalisation.
- *Lemma*: same stem, part of speech, rough word sense
- * cat and cats = same lemma _cat_
- *Wordform*: the full inflected surface form
- * cat and cats = different wordforms
##### Word Types vs Tokens:
**Example:** 
> they lay back on the San Francisco grass and looked at the stars and their
* *Type*: an element of the vocabulary. [the the = 1] 13 types (or 12) (or 11?) *V* = vocabulary |V| size of the vocabulary 
* *Token*: an _instance_ of that type in running text. 15 tokens (or 14 if San Francisco = 1) *N* = number of Tokens
*corpus (plural corpora)* = a couple of datasets of text
Get all the **Vocabulary** of a text `corpora.txt` sorted by frequency 
```bash
tr 'A-Z' 'a-z' < corpora.txt | tr -sc 'A-Za-z' '\n' | sort | uniq -c | sort -n -r | less
```

##### Issues in Tokenisation
* Finland’s capital -\> Finland Finlands Finland’s 
* what’re, I’m, isn’t -\> What are, I am, is not
* Hewlett-Packard -\> Hewlett Packard ?
* state-of-the-art -\> state of the art ?
* Lowercase -\> lower-case lowercase lower case ?
* San Francisco -\> one token or two?
* m.p.h., PhD. -\> ??
* Chinese and Japanese no spaces between words. Multiple alphabets 
Maximum Matching (also called Greedy): matches the largest match from the beginning of the word. Works well for Chinese
#### Word Normalisation
Implicitly define equivalent class of terms: U.S.A. = USA
Reducing letters to lower case with a few exceptions such as words with caps in the middle of the sentence
Lemmatising 
* am, are, is -\> be
* car, cars, car’s, cars’ -\> car
##### Morphology
* The small meaningful units that make up words
* *Stems*: The core meaning-bearing units 
* *Affixes*: Bits and pieces that adhere to stems (often with grammatical functions)
* Ex: meaning|ful -\> stem|affix, unit|s -\> stem|affix, Stem|s, affix|es, etc…
###### Stemming
Reduce terms to their stems. 
e.g., automate(s), automatic, automation all reduced to automat
The most common English stemmer *Porter’s algorithm* bunch of rules (steps) to remove most of the affixes.
#### Sentence Segmentation
Saber cuándo una frase termina para separar el corpus en frases.
No es suficiente con separar por los ‘.’ porque no siempre significan end of sentence. Para eso se puede ir todo lo complejo que quieras desde utilizar un decission tree sencillo hasta SVM y NN.

### Reading assignment
#### Text normalization
Normalizing text means converting it to a more convenient, standard form.
**Tokenization**: separating out or tokenizing words from running text. Using just white spaces as separators is not enough because some words separated by spaces are sometimes treated as large words e.g. _New York_ and _rock’n roll_. Tweets for example need emoticon and hashtag tokenization and Chinese has no spaces between words.
**Lemmatization**: the task of determining that two words have the same root, despite their surface differences. e.g. _sang_, _sung_, and _sings_ are forms of the verb _sing_. 
**Stemming**: refers to a simpler version of lemmatization in which we mainly just strip suffixes from the end of the word.
**Sentence segmentation**: breaking up a text into individual sentences, using cues like periods or exclamation points.
**Edit distance** It's a metric that measures how similar two strings are based on the number of edits (insertions, deletions, substitutions) it takes to change one string into the other. Used for example in _spelling correction_ and coreference resolution.

**Byte-Pair Encoding** is a very good algorithm to lemmatize and tokenize. Robust against unknown words
##### Words
###### Spoken speech
**Utterance** a spoken word or sentence “pronunciación”
**Disfluency** algo que se sale de la normalidad o del vocabulario, cosas como _fragments_ o _filled pauses_ 
**Fragment** palabras rotas o incompletas como main- mainly 
**Filled pause** words like _uh_ and _um_

###### Corpora
The world has 7097 languages. Dentro de estos lenguajes existen dialectos y encima existe el _code switching_ que consiste en usar palabras de otros idiomas en la misma frase. También existe el genre que es en qué contexto sale el texto. No se habla igual en una película que en la calle. Age, gender, race, socio-economic class can all influence the linguistic properties of the text we are processing. Its important to consider who produced the language, in what context, for what purpose, and make sure that the models are fit to the data.

###### Minimum Edit distance
minimum edit distance between two strings is defined as the minimum number of editing operations (operations like insertion, deletion, substitution) needed to transform one string into another. e.g. The gap between intention and execution, for example, is 5 (delete an i, substitute e for n, substitute x for t, insert c, substitute u for n).

## Week 2 - Language Models & Lexicons (pre-deep learning)

## Week 3 - Word Embeddings (Word, sentence, and document)

## Week 4-5 - Deep Sequence Modeling

## Week 6 - Dialogue Systems

## Week 7 - Transfer Learning

## Week 8 - Future NLP


Pytorch