## Quality control and filtering
[[He-2020-Assessing the Impact of Data Preprocessing on Analyzing Next Generation Sequencing Data.pdf]]

In this text I would like you to focus on the outcome of the study:
    - _Which tools are better for data processing, and which tools are equivalent?_
    - _How much does the choice of filtering tools affect the end result?_
    - _What could that mean for your projects?_

### Results
No significant difference in the impact on data quality after data preprocessing.

Frequency of mutations detected after data preprocessing may be affected. [...] The results of Trimmomatic data pretreatment were basically consistent with the raw sequencing data, and the results of Cutadapt and FastP data pretreatment were consistent. It showed that there were no significant differences in the four methods of mutation support reads number. However, the sequencing depth of the mutation sites were quite different.

Data preprocessing may affect HLA typing analysis. [...] incorrect typing results with the data after pretreatment of Cutadapt and FastP. [...] The results of the raw data and Trimmomatic data preprocessing were consistent with the validation results.

### Discussion
In this study, we compared commonly used data preprocessing software and found differences in the detection of hotspot mutations and HLA typing. [...] But most methods for the strategy of data preprocessing are to cut off all subsequent bases as long as the average quality of the bases in a certain bin or consecutive bases is below a certain threshold [...]. They do not notice the distribution of the actual low-mass bases in the sequence, which could result in many short sequences and may reduce the accuracy of downstream alignment and increase the sequencing depth of some reference sites. Thus, the analysis results may be inaccurate, and the effect may not be as good as the result of not doing data preprocessing, which was also confirmed in our analysis results. As the sequencing throughput becomes higher and higher, the sequencing read length becomes longer and longer, but the longer the sequencing read length, the worse the sequencing quality. Therefore, data preprocessing becomes increasingly important in data analysis.

## Mapping
[[Schbath-2012-Mapping Reads on a Genomic Sequence.pdf]]

Read the overview of the algorithms, particularly focusing on:
-  2.1 Hashing
- 2.2 Burrows-Wheeler alignments

What can you learn from the tool evaluation in Tables 3, 4, 5, 6, 7 and 8?

What from this study can you put to use in your projects?

### 2.1 Hashing
#### 2.1.1 Basic algorithms
Use sequences of length k and map them to the genome, recording each positions which it matches. Then you are able to search in the list of these k-mers for a match, and then extend around this position in the genome (*seed and extend*)

Modern sequencers are able to produce up to 1 billion reads in a single run, as a consequence current mapping tools now hash the genome.
#### 2.1.2 Improvements
Major drawback of *seed and extend*: to allow more errors the reads need to be split into smaller and smaller pieces, which can map to more positions in the genome. Able to use *spaced seeds* which contain "don't care" positions where the algorithm doesn't check the type of nucleotide present.

Most of the time spent by a seed and extend algorithm is spent in the "extend" part. 

## Assembly
[Ben Langmead's video series on mapping algorithms](https://www.langmead-lab.org/teaching.html#computational-genomics), subheading "Assembly"
