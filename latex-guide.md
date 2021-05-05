---
title: 10 Steps to Better LaTeX at the Unix Command Line and a Better Scientific Paper
author: Luke Olson and Jake Bowers
---

This guide shows you how to write a scientific article using the LaTeX document
preparation and markup system. We emphasize typing commands at the unix command
line in this guide as a way for you to see what is happening under the hood of
the LaTeX engine. We provide some links to graphical interfaces to LaTeX at the
end of the document.


# The structure of a document

A LaTeX document (or a .tex file) is a [plain text]() document that contains
commands to the LaTeX processing programs that instruct it how to create a
beautiful pdf. The following figure explains at a high level what the parts of
the document do.

![The Structure of a LaTeX document\label{fig:struct}](document_structure.png)


## Practice:

See the directory `1_structure` in the associated github repository (You can
practice typing these commands in the command line by clicking on the `launch
binder` button on that repository, and then clicking on the `Terminal` icon in
the Jupyter Lab SOMETHING pane.

# 2.  tex, latex,  pdflatex, etc ... basic gist

## tex: a program that typesets TeX directives or macros

## pdftex: a program that generates a PDF (instead of DVI)

## latex: a program that typesets a pile of LaTeX macros to make things easier

## pdflatex: a program that generates a PDF

## xelatex: support for a wide variety of fonts and characters

## lualatex: extends latex more of a programming language (via Lua)Two take-aways:always use LaTeX: very rarely (if ever) should you need to dip into TeXalways use PDF output (

## pdflatex) and PDF figures (or PNG … more on this later)pdflatex example.texbibtex examplepdflatex example.texpdflatex example.texmark

## cite{} entries in

## example.auxgenerate formatted

## .bbl file of citationsadd bibliography with labelsmap labels to

## cite{} in

## example.auxadd labels in the document

## pdflatex takes several passesTools like

## latexmk automate this!see

## 2_texflavors

# 3. LaTeX workflows

## Directory structure: [Zen of Python]()

## Simple is better than complex.

## Complex is better than complicated.

## Flat is better than nested.Commit to somethingSeparate:Data collection or raw data  (e.g.

## data1.db, …

## datan.db)Parsed or processed data (e.g.

## data_merged_filtered.db)Plotting data (e.g.

## temp_vs_time.csv)Plotting script (e.g.

## temp_vs_time.py)One Figure &lt;—&gt; One Script

## temp_vs_time.pdf &lt;—&gt;

## temp_vs_time.py

## LaTeX labelling:

## label{fig:temp_vs_time}paper_topic_name                        #  string used for repo, tex, and bib files+   requirements.txt                    # document number of pages, does that include refs, etc+-- 1_submitted_paper|   +-- paper_topic_name.tex|   +-- refs_topic_name.bib|   +-- journal_class.cls               # any files needed for the journal latex style|   +-- figures|   |   +-- temp_vs_time.pdf            # descriptive names for figures (not fig1.pdf, etc)|   |   +-- error_vs_stepsize.pdf|   |   `-- ...|   +-- data                            # data files that generate the figures|   |   +-- Makefile                    # Makefile that will re-generate all figures|   |   +-- temp_vs_time.csv            # use the same name as the resulting figure|   |   +-- plot_temp_vs_time.py        # plotting scripts, use names like plot_.py|   |   `-- ...|   `-- submitted_paper_topic_name.pdf  # actual PDF file submitted+-- 2_reviews|   +-- review_1.pdf                    # individual reviews|   +-- review_2.pdf|   `-- editor_statement.pdf            # instructions and summary from editor+-- 3_response_to_reviews|   +-- response_topic_name.tex|   `-- sent_response_topic_name.pdf    # actual PDF file sent to editor`-- 4_revised_paper    +-- paper_topic_name_revised.tex    +-- refs_topic_name_revised.bib    +-- journal_class.cls               # copy here any other files needed    +-- figures                         # copy here all the figures again    |   +-- temp_vs_time.pdf            # edit figures as needed    |   +-- error_vs_stepsize.pdf    |   `-- ...    +-- data                            # copy all data again and edit as needed    |   `-- ...    `-- submitted_paper_topic_name_revised.pdf  # actual PDF submittedReference: Matt West @ https://lagrange.mechse.illinois.edu/latex_quick_ref/Copy&amp;Pastesee

## 3_workflows

# 4. git version controlUse it!What to track:Your

# .tex file :)The

## .bib fileFigures -&gt;

## ./figures/*.pdfScripts for the figures -&gt;

## ./data/*.pyData for the figures -&gt;

## ./data/*.csvWhat not to track:The pdf of the paper -&gt;

## paper_randnoise.pdfAny typesetting output -&gt;

## *.log, *.bbl, *.aux, etcTips:Agree with your co-authors on one of one sentence per linehard wrapping at say 80 charactersnothing, free for allCommit *often*For large edits, take sections at a time, to reduce merge conflictssee

## 4_git

# 5. Journal StyleThe journal will have a style file

## Example:

## https://www.siam.org/publications/journals/about-siam-journals/information-for-authors#dnn_ctr2112_ContentPaneThe journal will also have a style *guide*

## Example:

## https://www.siam.org/Portals/0/Publications/Journals/stylemanual/SIAM_STYLE_GUIDE_2019.pdfFollowing both of these will speed up the review and copy editing.see

## 5_style

# 6. On WritingMore of an interlude…Use linters (what?)Mark open items and second pass items with

## %TODOgrep TODO paper_randnoise.texClear contributions, Outline, Write/RevisePolish and make it look visually appealing to read

## Remember: Peer reviewed publications are critically important to science — treat your presentation with care

## Remember: Peer reviewed publications take reviewer/editor time — treat your presentation with care

## Remember: (Hopefully) Many people will read your publication — treat your publication with caresee

## 6_linting

# 7. LaTeX dos and don’tsFact, not opinion! :)

##  DO keep your LaTeX readable!Block indent equationsAlign tabular dataLimited whitespace

## DON’T overuse macrosIntended for complex arrangements with repeated useThings that might change.

## DO attach a float environment after the paragraph of first referenceGenerally use

## [!ht]

## !: tex will ignore area restrictions

## h: place it “here” if it fits in the area

## t: place it at the “top” otherwise and if it fitsotherwise create a new page

## DON’T use

## FloatBarrier and other tricks to for spacingnewpage, vspace, hspace

## DO use packages for consistent layouts

## booktabs: clean tabular

## siunitx: large numbers and notation

## DON’T use

## align for everything

## equation: base

## align: multiple equations

## split: one equation split with alignment

## multline: one equation split with no alignment

## DO use consistent fonts throughout (more on this…)Label figures with

## label{fig:*}Label equations with

## label{eq:*}Label sections with

## label{sec:*}Label tables with

## label{tb:*}see

## 7_dos

# 8. On bibtexBibtex: a program and a format for specifying bibliography entriesJournals specifying the formatting rulesSeveral typesBy id: [7]By name [Olson 2021] or [Ol21]Can be unsorted or listed by order of reference in the paperThe journal

# .bst defines the required fieldsGeneral workflow:Grab full citation online at citation’s journalClean up entry (removing abstracts or other fields)Format cleanly.  Use

## { } vs

## “ “

## { } also force capitalization:

## title = {All about {Krylov} methods}pdflatex paper_randnoise.texbibtex paper_randnoisepdflatex paper_randnoise.texpdflatex example.texmark

## cite{} entries in

## paper_randnoise.auxgenerate formatted

## .bbl file of citationsadd bibliography with labelsmap labels to

## cite{} in

## paper_randnoise.auxadd labels in the documentpaper_randnoise.auxsiamplain.bstrefs_paper_randnoise.bibformatted

## .bbl filesee 2

## _bibtex

# 9. On FiguresFonts in figures should match the fonts in the float/article.

# includegraphics[width=0.3textwidth]{./figures/myfig.pdf} also scales the fonts — be careful!Use consistent color schemes throughout the paperLabel everythingDo not introduce new notation in a figure or its captionThe figure caption should describe, not discuss.A terrible figure!see

## 9_figures

# 10. Helpful tools

# tikz: sharp figures and schematics in LaTeX

## tikzpdf: build/rebuild tikzpictures

## https://github.com/lukeolson/tikzpdf

## latexrun: compile and summarize warnings

## chktex: a LaTeX linter

## betterbib: automatically format/update your bib entries

## https://github.com/nschloe/betterbib

## illinois-letterhead: a letterhead in LaTeX

## https://github.com/lukeolson/illinois-letterheadscrub your LaTeX and submit to Arxiv:

## https://github.com/lukeolson/clean-latex-to-arxiv.git

## booktabs: nice looking tables

## siunitx: nice looking numbers and units

## algorithm2e: algorithm environment

## cleveref: cref{} referencing for all

## hyperref: hyper linkes to figures, etc

## backref: add page numbers to the bibmicrotype

## http://www.khirevich.com/latex/microtype/enumitemfull control of itemize environments




# Collaborate Asynchronously using Github

See.... 

# Collaborate Synchronously using...

There are several tools that allow collaborators to edit plain text documents at the same time.

Some like [Overleaf]() because it compiles LaTeX.

Others like [Teletype for Atom](https://teletype.atom.io).

Or [Hedgedoc]()

Or [TeXPad Connect]()

Or even Google Docs.




# Extra:

Our friends who use LaTeX like the following systems. Each person prefers to interact with their computer differently, so we merely list what we've heard about here.

 -  [Emacs with Auctex](https://kevinlanguasco.wordpress.com/2019/04/29/latex-editing-with-emacs-on-manjaro/)
 -  [Neovim or Vim with vimtex or texlab]
 -  [TexPad]
 -  [TexShop]
 -  [TeXstudio]

# References
