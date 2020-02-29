---
#####################
## thesis metadata ##
#####################
title: |
  Flexibility in avian \
  migration across scales
author: Benjamin Mark Van Doren
college: Somerville College
degree: Doctor of Philosophy
degreedate: Hilary 2020
abstract: |
  This *R Markdown* template is for writing an Oxford University thesis. The template is built using Yihui Xie's `bookdown` package, with heavy inspiration from Chester Ismay's `thesisdown` and the `OxThesis` \LaTeX\ template (most recently adapted by John McManigle).
  
  This template's sample content include illustrations of how to write a thesis in R Markdown, and largely follows the structure from [this R Markdown workshop](https://ulyngs.github.io/rmarkdown-workshop-2019/).
  
  Congratulations for taking a step further into the lands of open, reproducible science by writing your thesis using a tool that allows you to transparently include tables and dynamically generated plots directly from the underlying data. Hip hooray!
acknowledgements: |
  This is where you will normally thank your advisor, colleagues, family and friends, as well as funding and institutional support. In our case, we will give our praises to the people who developed the ideas and tools that allow us to push open science a little step forward by writing plain-text, transparent, and reproducible theses in R Markdown. 
  
  We must be grateful to John Gruber for inventing the original version of Markdown, to John MacFarlane for creating Pandoc (<http://pandoc.org>) which converts Markdown to a large number of output formats, and to Yihui Xie for creating `knitr` which introduced R Markdown as a way of embedding code in Markdown documents, and `bookdown` which added tools for technical and longer-form writing.
  
  Special thanks to [Chester Ismay](http://chester.rbind.io), who created the `thesisdown` package that helped many a PhD student write their theses in R Markdown. And a very special tahnks to John McManigle, whose adaption of Sam Evans' adaptation of Keith Gillow's original maths template for writing an Oxford University DPhil thesis in \LaTeX\ provided the template that I adapted for R Markdown.
  
  Finally, profuse thanks to JJ Allaire, the founder and CEO of [RStudio](http://rstudio.com), and Hadley Wickham, the mastermind of the tidyverse without whom we'd all just given up and done data science in Python instead. Thanks for making data science easier, more accessible, and more fun for us all.
  
  \begin{flushright}
  Ulrik Lyngs \\
  Linacre College, Oxford \\
  2 December 2018
  \end{flushright}
# dedication: For Yihui Xie
# abbreviations: "front-and-back-matter/abbreviations" # path to .tex file with abbreviations

#######################
## bibliography path ##
#######################
bibliography: references.bib
bibliography-heading-in-pdf: References

#####################
## PDF formatting  ##
#####################
abstractseparate: true  # include front page w/ abstract for examination schools?
bib-humanities: true   #set to true if you want in-text references formatted as author-year
doi-in-bibliography: true #set to true if you want DOI's to be shown in the bibliography
draft: true # add as DRAFT mark in the footer?
page-layout: 'twoside' #'nobind' for PDF output (equal margins), 'twoside' for two-sided binding (mirror margins and blank pages), leave blank for one-sided binding (left margin > right margin)
hidelinks: true #if false, the PDF output highlights clickable links with a colored border - you will probably want to set this to true for PDF version you wish to physically print
toc-depth: 2 # depth of heading to include in table of contents
lof: true # list of figures in front matter?
lot: true # list of tables in front matter?
mini-toc: true  # mini-table of contents at start of each chapter? (this just prepares it; you must also add \minitoc after the chapter titles)
mini-lot: false  # mini-list of tables by start of each chapter?
mini-lof: false  # mini-list of figures by start of each chapter?

params:
  corrections: true # set false to stop applying blue background to blocks of corrections

#####################
## output options  ##
#####################
output:
  bookdown::pdf_book:
    template: templates/template.tex
    keep_tex: true
    citation_package: biblatex  
    pandoc_args: ["--lua-filter=scripts_and_filters/correction_filter.lua"] #remove filter to stop applying blue background to inline corrections
  bookdown::gitbook:
    css: templates/style.css
    config:
      sharing:
        facebook: false
        twitter: yes
        all: false
  bookdown::word_document2:
    toc: true   
link-citations: true
documentclass: book

---



<!--
Include the create_chunk_options chunk above at the top of your index.Rmd file
This will include code to create additional chunk options (e.g. for adding author references to savequotes)
If you need to create your own additional chunk options, edit the file scripts/create_chunk_options.R
-->




# Introduction {-}

\adjustmtc 
<!-- For PDF output, we must include this LaTeX command after unnumbered headings, otherwise the numbers in the mini table of contents will be incorrect -->

<!-- this adds an image in gitbook output --> 
<img src="figures/cover.png" width="315" height="445" alt="Cover image" align="right" style="margin: 0 1em 0 1em" />

Welcome to the *R Markdown* Oxford University thesis template. 
This sample content is adapted from [`thesisdown`](https://github.com/ismayc/thesisdown) and the formatting of PDF output is adapted from the [OxThesis LaTeX template](https://github.com/mcmanigle/OxThesis). 
Hopefully, writing your thesis in R Markdown will provide a nicer interface to the OxThesis template if you haven't used TeX or LaTeX before.
More importantly, using *R Markdown* allows you to embed chunks of code directly into your thesis and generate plots and tables directly from the underlying data, avoiding copy-paste steps. 
This will get you into the habit of doing reproducible research, which benefits you long-term as a researcher, but also will greatly help anyone that is trying to reproduce or build upon your results down the road.

Using LaTeX together with *Markdown* is more consistent than the output of a word processor, much less prone to corruption or crashing, and the resulting file is smaller than a Word file. 
While you may never have had problems using Word in the past, your thesis is likely going to be about twice as large and complex as anything you've written before, taxing Word's capabilities.

## Why use it? {-}
*R Markdown* creates a simple and straightforward way to interface with the beauty of LaTeX.
Packages have been written in **R** to work directly with LaTeX to produce nicely formatting tables and paragraphs. 
In addition to creating a user friendly interface to LaTeX, *R Markdown* allows you to read in your data, analyze it and to visualize it using **R**, **Python** or other languages, and provide documentation and commentary on the results of your project.  
Further, it allows for results of code output to be passed inline to the commentary of your results.
You'll see more on this later, focusing on **R**. If you are more into **Python** or something else, you can still use *R Markdown* - see ['Other language engines'](https://bookdown.org/yihui/rmarkdown/language-engines.html) in Yihui Xie's [*R Markdown: The Definitive Guide*](https://bookdown.org/yihui/rmarkdown/language-engines.html).

<!-- 
Having your code and commentary all together in one place has a plethora of benefits!
-->

## Who should use it? {-}
Anyone who needs to use data analysis, math, tables, a lot of figures, complex cross-references, or who just cares about reproducibility in research can benefit from using *R Markdown*. 
If you are working in 'softer' fields, the user-friendly nature of the *Markdown* syntax and its ability to keep track of and easily include figures, automatically generate a table of contents, index, references, table of figures, etc. should still make it of great benefit to your thesis project.
