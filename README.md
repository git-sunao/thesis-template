# Thesis template
This is a thesis template for the Department of Physics, Faculty of Science & Graduate School of Science, The University of Tokyo.
This template is written by [Sunao Sugiyama](https://git-sunao.github.io/). 
I appreciate if you can acknowledge me for the use of this template.

## Structure
- [contents](contents): This directory is for thesis contents (tex file).
- [figures](figures)  : Put figures under this directory.
- [tables](tables)    : Put tables under this directory.
- [bst](bst)          : Put your bib file under this directory. This directory also includes bst files.
- [misc](misc)        : This directory includes miscellaneous files, e.g. logo of your institute.
- [sty](sty)          : This directory includes some style files. 

## Files you need to modify
- [abstract.tex](sty/abstract.tex): This file formats the abstract.
- [title.tex](sty/title.tex)      : This file formats the title page of thesis.
- [backcover.tex](backcover.tex)  : This is used when you want to make the back cover.
- [phd.sty](sty/phd.sty)          : Define frequentry used commands.
- [packages.sty](sty/packages.sty): Declare packages you use for the thesis.  

## How to compile
### Basic use
To compile the thesis, run the command below.
```bash
latexmk -pdfdvi main
```

### Print print version
If you want to compile a print version thesis, comment-out line 7, 
uncomment-out line 9 of [packages.sty](sty/packages.sty), and then run the same command.
This makes makes the spaces leftside (rightside) on even (odd) pages.

### Back cover
```bash
latexmk -pdfdvi backcover
```
To clean-up unnecessary files, run
```bash
latexmk -c
```
or
```bash
latexmk -C
```

### Abstract
University of Tokyo requires an abstract file as a separated document from the main thesis (at least for PhD thesis). You can compile the abstract with
```bash
latexmk -pdfdvi abstract
```
Also, Japanese version can be compiled with
```bash
latexmk -pdfdvi abstract_ja
```

## Tips
### Getting error for the first compile
When I got the following error message
```
...
Rule 'makeindex main.idx': The following rules & subrules became out-of-date:
  makeindex main.idx
------------
Run number 1 of rule 'makeindex main.idx'
------------
------------
Running 'mendex  -o "main.ind" "main.idx"'
------------
This is mendex version 3.6 [19-Sep-2021] (utf8.uptex) (TeX Live 2022).
Scanning input file main.idx....done (0 entries accepted, 0 rejected).
0 entries accepted, 0 rejected.
Nothing written in output file.
Latexmk: Errors, so I did not complete making targets
Collected error summary (may duplicate other messages):
  makeindex main.idx: Command for 'makeindex main.idx' gave return code 65280
      Refer to 'main.ilg' for details
Latexmk: If appropriate, the -f option can be used to get latexmk
  to try to force complete processing.
```
I solved this by running
```
makeindex main.idx
```
This makes a lot of `main.mtc[number]` files.

### Warning at href for section including math
When you get ``Package hyperref Warning: Token not allowed in a PDF '', follow https://tex.stackexchange.com/questions/251491/math-symbol-in-section-heading
% \texorpdfstring{}{}


### Merging two bib files
See [stackoverflow](https://tex.stackexchange.com/questions/20027/merge-two-bibtex-files). Bibtool can be installed via [brew](https://formulae.brew.sh/formula/bib-tool).
bibtool -s -d bib1.bib bib2.bib
