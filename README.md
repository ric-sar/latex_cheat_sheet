![latex_logo](https://user-images.githubusercontent.com/82369153/216924875-a95e02b0-020e-4169-99c0-ceb1107c54ac.png)
<div align="center">This repo is meant to be a useful non-comprehensive LaTeX Cheat Sheet that you will use while writing a LaTeX document.<br>
For everything alse go to the dedicated <a href="https://en.wikibooks.org/wiki/LaTeX">LaTeX Wikibook page</a> or <a href="https://tex.stackexchange.com/">StackExchange page.</a>.<br>
For TeX materials (e.g., package details) visit the <a href="https://www.ctan.org/">Comprehensive TeX Archive Network (CTAN)</a>.<br>
For starters, I recommend to read first <a href="https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes">Learn LaTeX in 30 minutes</a>
</div>

---

**Table of contents**
- [Online vs Offline](#online-vs-offline)
- [Text](#text)
  * [Bold](#bold)
  * [Italic](#italic)
  * [Underline](#underline)
  * [Change color](#change-color)
  * [Formatting mix](#formatting-mix)
  * [Highlight](#highlight)
    + [Bypass citation](#bypass-citation)
    + [Bypass reference](#bypass-reference)
- [Figure](#figure)
    + [Single figure](#single-figure)
    + [Multiple sub figures](#multiple-sub-figures)
      - [1x2](#1x2)
      - [2x2](#2x2)
- [Table](#table)
    + [Simple table](#simple-table)
    + [Complex table](#complex-table)
- [Math](#math)
    + [How to split math equation on multiple lines with split](#how-to-split-math-equation-on-multiple-lines-with-split)
    + [How to split math equation on multiple lines with align](#how-to-split-math-equation-on-multiple-lines-with-align)
- [Bibliography](#bibliography)
  * [How to properly cite an arXiv contribution on IEEE](#how-to-properly-cite-an-arxiv-contribution-on-ieee)
- [How to add citation and reference](#how-to-add-citation-and-reference)
- [Useful misc arguments](#useful-misc-arguments)
  * [Show page layout](#show-page-layout)
  
---

# Online vs Offline
If you are a fresh LaTeX user, choosing the right TeX editor for the first time is not an easy task. In my opinion the best way to approach LaTeX is by using [Overleaf](https://www.overleaf.com/).
Overleaf is an online and collaborative LaTeX editor, which means that you only need a web browser and an Internet connection to work. You do not need to configure or install nothing, just create an account and start creating a new project, Overleaf will handle everything for you. The free account is enough for starters, if you need more compile timeout or want to add more collaborators to the project or integrations with [GitHub](https://github.com/), [Dropbox](https://www.dropbox.com), [Mendely](https://www.mendeley.com/) or [Zotero](https://www.zotero.org/) check the [Plans and Pricing section](https://www.overleaf.com/user/subscription/plans).

While, if you are a geek and want to have everything under control you can choose between many editors like: [Texmaker](https://www.xm1math.net/texmaker/), [TeXWorks](https://www.tug.org/texworks/), [Lyx](https://www.lyx.org/Home) or [TeXStudio](https://texstudio.sourceforge.net/).
On the other hand is possible to host a [community edition of Overleaf](https://github.com/overleaf/overleaf) on your on server.

It is worth to mention alternatives like: [Papeeria](https://papeeria.com/), [Authorea](https://www.authorea.com/) or [CoCalc](https://cocalc.com/).

# Text
Here we present basic text formatting:

### Bold
To bold text in LaTeX we simply use the command ```\textbf{This text is in bold}```.

### Italic
To format text in Italic just use the command ```\textit{It's-a me, Mario!}```.

### Underline
The same apply to underline text with the command ```\underline{Text underlined}```.

### Change color
Sometimes we need to change color of text parts, we only need to use the ```xcolor``` package.
Require package:
```
\usepackage{xcolor}
```
And inside the text we apply the color, e.g., ```this text is not in red and \textcolor{red}{this text is in red}```.
The color can be changed inside the command ```\textcolor{color_to_use}```.

Further colors and commands to used inside the ```textcolor``` package can be found [here](https://ctan.mirror.garr.it/mirrors/ctan/macros/latex/contrib/xcolor/xcolor.pdf).

### Formatting mix
Combining commands will help us to a format mix, for istance we want to underline and bold a text we will use ```\underline{\textbf{This text is underlined and bold}}```.

## Highlight
Highlighting text is fundamental, espercially during a paper review will be requested to highlight all the changes.
Required packages:
```
\usepackage{soul}
\usepackage{xcolor}
```
With ```soul``` we can highlight text lightning fast with ```\hl{text to highlight}``` command, when we will not need the highlights just put the package into comment with ```%\usepackage{soul}``` and all the highlights will disappear without generating errors or warnings.
The default highlighting color is yellow, it can be changed by setting the color as ```\sethlcolor{color_name}``` (i.e., for highlighting in red ```\sethlcolor{red}```).

But what happen if we want to highlight citations or references?

### Bypass citation
To highlight citations and bypass all the warnings we need to put a ```\mbox``` command like this:
```
\mbox{\cite{paper_to_cite}}
```

### Bypass reference
While, highlighting references (like figures, tables or math equations) is much easier, just put the reference between curly brackets to avoid warnings like so:
```
\hl{Fig. {\ref{fig:figure_to_refer}}}
```

# Figure
Some read the text others look at the pictures. And we should be able to plot figures on a LaTeX document:

Package required:
```
\usepackage{graphicx}
```
### Single figure
![single_figure](https://user-images.githubusercontent.com/82369153/216826809-b88f1882-fe25-4338-96b9-008813f1a8fd.png)
```
\begin{figure}[ht]
  \centering
    \includegraphics[width = 1\textwidth]{example-image}
  \caption{Insert caption here.}
  \label{fig:figure_name}
\end{figure}
```
The figure is added by using ```\includegraphics``` command which takes as argument the size of the figure (that can be adjusted using the textwdith - e.g., by applying ```[width = 0.5\textwidth]``` the figure will be 50% of the textwidth) and the file path ```{example-image}```.
Then you can add the caption below the figure with ```\caption{Insert the caption here.}``` command and the label with ```\label{fig:figure_name}``` used as a reference in the text.
Also, the figure can be centered with the ```\centering``` command.

### Multiple sub figures
Ok, one single figure is easy stuff, what about muliple figures arranged like a grid?
One possible solution made by using the ```subcaption``` package:
```
\usepackage{graphicx}
\usepackage{subcaption}
```
#### 1x2
We can arrange the sub figures as we wish, in the following example two figures have been arranged side by side on the same row:
![sub_figure_1_2](https://user-images.githubusercontent.com/82369153/216826819-0bf53f43-e65f-46b6-82b2-e9d3d2f0b092.png)
```
\begin{figure}[ht]
  \centering
    \subfloat[Figure 1]
    {\includegraphics[height=2cm, width=2cm]{example-image}
    \label{fig:sub_figure_name}}
  \hfil
    \subfloat[Figure 2]
    {\includegraphics[height=2cm, width=2cm]{example-image}
    \label{fig:sub_figure_name}}
  \caption{Insert caption here.}
  \label{fig:figure_name}
\end{figure}
```
The main difference with the single figure is related to the sub figure added by ```\subfloat``` command, which takes as argument the caption related to the sub figure (e.g., ```\subfloat[Figure 1]```). While, ```\hfil``` command is used to set horizontal alignment in matrices and arrays. 
Then, a full caption and label can be referred to the entire figure or the single sub figures.

#### 2x2
In the following example more sub figures have been added by using the ```\subfloat``` command:
![sub_figure_2_2](https://user-images.githubusercontent.com/82369153/216826832-881dfc48-cb60-4e75-98c4-ad22e6e3d5d3.png)
```
\begin{figure}[ht]
  \centering
    \subfloat[Figure 1]
    {\includegraphics[height=2cm, width=2cm]{example-image}
    \label{fig:sub_figure_name}}
  \hfil
    \subfloat[Figure 2]
    {\includegraphics[height=2cm, width=2cm]{example-image}
    \label{fig:sub_figure_name}}

    \subfloat[Figure 3]
    {\includegraphics[height=2cm, width=2cm]{example-image}
    \label{fig:sub_figure_name}}
  \hfil
    \subfloat[Figure 4]
    {\includegraphics[height=2cm, width=2cm]{example-image}
    \label{fig:sub_figure_name}}
  \vspace{2mm}
  \caption{Insert caption here.}
  \label{fig:multiple_sub_figures_name}
\end{figure}
```
As you can see a vertical space of ```2mm``` has been added. The vertical space ```\vspace{2mm}``` has been applied between the last row and the caption.

# Table
Tables, tables and tables... The killer of every LaTeX student!

### Simple table
![simple_table](https://user-images.githubusercontent.com/82369153/216826847-5e341348-7c89-4140-8a65-27652e1e7f9b.png)
```
\begin{table}
  \centering
    \begin{tabular}{l|l|l}
     Col1 & Col2 & Col3  \\ 
     \hline
     Row1 & 1    & 2     \\
     Row2 & 3    & 4     \\
     Row3 & 5    & 6    
     \end{tabular}
  \caption{Insert caption here.}
  \label{tab:table_name}
\end{table}
```
The table begin with ```\begin{table}``` command but its content is defined by ```\begin{tabular}{}``` command which defines the table spec inside curly brackets, in the provided example there are three left-justified columns ```\begin{tabular}{l|l|l}``` (the ```l``` stands for left-justified, ```c``` centered and ```r``` right-justified) separated by vertical lines (the ```|``` create borders within columns).
The column name is defined and separated by ```&``` command while ```\\``` command starts a new row (e.g., ```Col1 & Col2 & Col3  \\```).
The ```\hline``` command adds the horizontal separation line between column name and data.
Now, let's imagine to build and fill a more complex and full-data table, the work will be annoying and prone to human error.

### Complex table
Tables are not easy to manage, I recommend to use the following web-tools (for instance you can upload or copy-paste the data from Excel files):
* [LaTeX Tables Editor](https://www.latex-tables.com/)
* [Tables Generator](https://www.tablesgenerator.com/)

# Math
As for the tables, sometimes you need a visual tool to write math equations, the following links will help you in the process:
* [tutorialspoint - LaTeX Equation Editor](https://www.tutorialspoint.com/latex_equation_editor.htm)
* [CodeCogs - Online LaTeX Equation Editor - create, integrate and download](https://latex.codecogs.com/eqneditor/editor.php) 
* [HostMath - Online LaTeX formula editor and browser-based math equation editor](https://www.hostmath.com/)
* [Lagrida - Online LaTeX Equation Editor](https://latexeditor.lagrida.com/)

While, here you can find cheat sheets of math symbols:
* [Kapeli - LaTeX Math Symbols](https://kapeli.com/cheat_sheets/LaTeX_Math_Symbols.docset/Contents/Resources/Documents/index)
* [Tilburg ScienceHub - Cheatsheet for LaTeX Math Commands](https://tilburgsciencehub.com/building-blocks/collaborate-and-share-your-work/write-your-paper/amsmath-latex-cheatsheet/)

### How to split math equation on multiple lines with split
Sometimes you need to split a math equation on multiple lines, one possible way is to use the package ```amsmath``` to display equations and ```amsfonts``` which is an extended set of fonts for use in mathematics.
Required package:
```
\usepackage{amsmath}
\usepackage{amsfonts}
```
![eq_multiline](https://user-images.githubusercontent.com/82369153/216826870-ef2840c5-dcb3-47de-bd3d-9cc2002f114d.png)
```
\begin{equation}
    \begin{split} 
        \upsilon (s) = {\mathbb{E}}\left [ G_t | S_t = s \right ] \\
        = {\mathbb{E}}\left [ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + ...| S_t = s \right ] \\
        ... \\
        = {\mathbb{E}}\left [ R_{t+1} + \gamma \upsilon S_{t+1} | S_t = s \right ] 
    \end{split}
    \label{eq:eq_name}
\end{equation}
```
Write equations inside the ```split``` command and split equations with ```\\``` command to go to the new line.
The progressive number to reference the equation will be automatically inserted in the middle of the split.

### How to split math equation on multiple lines with align
Alternatively, you can use ```align``` to split equations.
```
\begin{align} 
    \upsilon (s) = {\mathbb{E}}\left [ G_t | S_t = s \right ] \nonumber \\ 
    = {\mathbb{E}}\left [ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + ...| S_t = s \right ] \nonumber \\
    ... \nonumber \\
    = {\mathbb{E}}\left [ R_{t+1} + \gamma \upsilon S_{t+1} | S_t = s \right ] \label{eq:eq_name}
\end{align}
```
The difference with ```split``` lives in adding the command ```\nonumber``` before going to a new line and the corresponding progressive number to reference the equation can be inserted where the user wants (i.e., in the corresponding line where the label is put, in the example in the last line). 

# Bibliography
Bibligraphy management is one of the best feature of LaTeX, just put these two lines at the end of the document
```
\bibliographystyle{ieeetr}
\bibliography{refs.bib}
```
Create a new file ```refs.bib``` where you will add all your citation and LaTeX will compile the bibliography for you!
Also, you can select within the seven bibliography styles without any effort: ```plain```, ```acm```, ```ieeetr```, ```alpha```, ```abbrv``` and ```siam```.

## How to properly cite an arXiv contribution on IEEE
If you have just started your adventure in the research field there is a high probabily that you have already encountered [arXiv](https://arxiv.org/). [arXiv](https://arxiv.org/) is a free distribution service and an open-access archive scholarly articles, although you can expoert directly the BibTeX formatted citation you need to properly cite the article by adding a the arXiv identifier to the note of the citation.
For instance, for the paper [Attention is all you need](https://arxiv.org/abs/1706.03762) the formatted citation is the following:
```
@misc{https://doi.org/10.48550/arxiv.1706.03762,
  doi = {10.48550/ARXIV.1706.03762},
  url = {https://arxiv.org/abs/1706.03762},
  author = {Vaswani, Ashish and Shazeer, Noam and Parmar, Niki and Uszkoreit, Jakob and Jones, Llion and Gomez, Aidan N. and Kaiser, Lukasz and Polosukhin, Illia},
  keywords = {Computation and Language (cs.CL), Machine Learning (cs.LG), FOS: Computer and information sciences, FOS: Computer and information sciences},
  title = {Attention Is All You Need},
  publisher = {arXiv},
  year = {2017},
  copyright = {arXiv.org perpetual, non-exclusive license}
}
```
Just add the related arXiv identifier with  ```note = {arXiv:1706.03762}```.

# How to add citation and reference
Adding citation and reference is the main and most profilic advantage of LaTeX and are the first commands that you will learn during your journey.
After having added your citation in the bibliography you can cite it just adding the following command in the text:
```\cite{what_we_want_to_cite}```

While, after having added your tables, figures, equations and so on, use the following command to add reference in the text:
```\ref{what_we_want_to_refer}```

As a trick, I suggest to you to add to the command ```\label{}``` a little tag to distinguish between figures, tables, equations, and so on.
E.g. figures can be labelled as ```\label{fig:figure_name}```, tables as ```\label{tab:table_name}``` or equations ```\label{eq:equation_name}```, this will help you during writing to remember to what object are adding the reference.

# Useful misc arguments
Here you will find useful misc arguments:

## Show page layout
While writing a paper (for instance in the traditional two-column layout) we might be interested if we can make better styling choice by knowing the margin of the chosen template. In this case the package showframe will help us:
```
\usepackage{showframe}

\renewcommand\ShowFrameLinethickness{insert_thickness}
\renewcommand*\ShowFrameColor{\color{insert_color}}
```
By adding the showframe package we decide how many points the frame thickness will be with the command ```\renewcommand\ShowFrameLinethickness{0.15pt}``` (i.e., for a frame of 0.15pt) and the corresponding color with the command ```\renewcommand*\ShowFrameColor{\color{red}}``` (i.e., for red frame).

The following is an example of [IEEE Access Template](https://www.overleaf.com/latex/templates/ieee-access-latex-template/cdxrhtbjgszv) with page layout borders:
![IEEE_Access_LaTeX_template_Pagina_1](https://user-images.githubusercontent.com/82369153/217602631-c06abbc8-65a3-4d1f-970b-85ca9d036949.jpg)
