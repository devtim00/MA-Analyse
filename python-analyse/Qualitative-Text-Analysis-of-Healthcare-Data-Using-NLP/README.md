# Qualitative Text Analysis using NLP
 
Qualitative text analysis is a common practice in clinical research. It is a process of analyzing qualitative text data, such as open-ended survey responses and interview transcripts and the general approach involves reading the data and manually assigning codes to text segments. A code is a concise label to identify the meaning in a segment of text e.g., `I like to exercise` might be coded by the experts as `exercise`. Qualitative text analysis is a relatively labor intensive process. Hence a pipeline is developed here using [`WordNet`](https://www.nltk.org/howto/wordnet.html), a natural language processing (NLP) tool to automate part of this process. 

The aim is to summarize the given healthcare text using Wordnet similarity. Specifically, the task is to get sematically similar clusters of terms from the given text data. The data is composed by collecting response over short message text from different participants for a given question. Hence each response is no more than 160 characters long including spaces. Questions were typically open-ended related to current events and some specific health concerns and participants were young adults aged 14-24 years.

We have applied both NLP and manual qualitative text analysis methods to a set of such text data. Eventually, we compare the utility of a traditional qualitative text analysis, an NLP analysis, and an augmented approach that combines qualitative and NLP methods. A team of clinicians from the University of Michigan Medical School in Ann Arbor, USA had collected the data and had done manual qualitative text analysis for further evaluation. I had developed the NLP framework with the inputs from another collaborator in Department of Learning Health Sciences at University of Michigan. 


The analysis and performance of this framework is explained in this paper:

[Timothy C Guetterman, Tammy Chang, Melissa DeJonckheere, Tanmay Basu, Elizabeth Scruggs and VG Vinod Vydiswaran. Augmenting Qualitative Text Analysis with Natural Language Processing: Methodological Study. Journal of Medical Internet Research, vol. 20(6), 2018.](https://www.jmir.org/2018/6/e231/).

`Note that this pipeline can be used for any such text summarization task.` 

## Prerequisites
[Python 3](https://www.python.org/downloads/), [NLTK](https://www.nltk.org/install.html)

## How to run the pipeline?

The model is implemented in `qualitative_text_analysis.py`. Run the following lines in a Python environment to get the summary of given data. 

```
clf=qualitative_text_analysis(path='/Users/basut/myvoice/what_qualities.txt',wordnet_metric='w',pos='b',transformation='d')
clf.get_summary()
```

Here `path` is the path of the given data. The data should be in a text file with '.txt' extension and each line of the file should not contain more than 160 characters including spaces. It is recommended to have 50 to 100 lines in the data file, but in principle, there is no limit on number of lines. The `output` will be stored in a csv file, named as `input_filename_summary.csv` and each row of the csv file will represent a cluster of terms. 

The following options of `Wordnet metrics` are available and the `default` is `Wu-Palmer similarity`:    

         "j" for Jiang-Conrath similarity
         
         "le" for Leacock-Chodorow (LCH) similarity
         
         "li" for Lin similarity
         
         "p" for Path similarity
         
         "w" for Wu-Palmer similarity 

The following options of `POS` i.e., parts of speech are available and the `default` option is `b`: 

         "a" for adjectives
         
         "b" for both adjectives and nouns
         
         "n" for nouns 

The options of `transformation` are "d" to generate `derivationally related form` of a term and "s" to perform `stemming` and the `default` option is `d`. An example code to run `qualitative_text_analysis` for the given data is uploaded as `test.py`. 

## Contact

For any further query, comment or suggestion, you may reach out to me at welcometanmay@gmail.com

## Citation
```
@article{guetterman18,
  title={Augmenting qualitative text analysis with natural language processing: methodological study},
  author={Guetterman, Timothy C and Chang, Tammy and DeJonckheere, Melissa and Basu, Tanmay and Scruggs, Elizabeth and Vydiswaran, VG Vinod},
  journal={Journal of Medical Internet Research},
  volume={20},
  number={6},
  pages={e231},
  year={2018},
  publisher={JMIR Publications Inc., Toronto, Canada}
}
```
