# Differential expression analysis with DESeq2

updated 2024-05-28

## Goal
A common bioinformatics task is to identify features (eg., differentially expressed genes) in a genomics dataset (eg., RNA-seq of many samples) which are significantly different between phenotypes (eg., experimental and control treatments). 
In the differential expression use case, a simple approach might be to perform a t-test between *GENE* expression values in experimental and control samples, correcting for multiple hypotheses if necessary.[^1] However, the differential expression use case   
is common enough that a number of statistical tools have been developed specifically for this task.[^2] Here we use DESeq2.[^3]

## Dependencies

This tutorial uses `conda`, `jupyter`, and of course the `DESeq2` R package.

## Installation
```
conda create -n deseq2
conda activate deseq2
# conda config --env --set subdir osx-64  # uncomment this line if using a Mac with Apple silicon.
conda install bioconductor-deseq2 r-irkernel
R -e 'IRkernel::installspec(name="deseq2",displayname="deseq2")'
```

## Tutorial

Much of this tutorial is adapted from [the official DESeq2 tutorial](https://www.bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html). 
Open the `deseq2.ipynb` jupyter notebook in this directory to continue the tutorial, setting the kernel to the "deseq2" kernel we just set up. 
See [0_Setting_up_your_workstation](../0_Setting_up_your_workstation) for instructions on how to set up jupyter.

## Footnotes

[^1]: *Multiple hypothesis correction.* If you test more than one hypothesis in an experiment, best practice is to adjust the p-value threshold at which we call a significant positive result. The intuition for this practice is as follows: suppose we were to test 
20,000 genes for differential expression between a random segregation of identically treated samples. Because there is no true biological difference, the true number of differentially expressed genes is zero. However, the number of positive results in our test 
would be (number of tests) x (p-value threshold) = 20000 x 0.05 = 1000. In other words, if the null hypothesis is true and we perform 20,000 tests, we can expect a thousand false positive results. 
  To limit the number of false positives reported, we set a stricter threshold for reporting a positive result. I usually use *Benjamini-Hochberg correction*, which is implemented in the `statsmodels` package and many others including `DESeq2`. The resulting
  value after multiple hypothesis correction is called an "adjusted p-value" or "q-value".

[^2]: Besides `DESeq2`, the R packages `limma`, `edgeR`, and `sleuth` are commonly used for differential expression analysis.

[^3]: [Love, M.I., Huber, W. & Anders, S. Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. Genome Biol 15, 550 (2014).](https://doi.org/10.1186/s13059-014-0550-8)
