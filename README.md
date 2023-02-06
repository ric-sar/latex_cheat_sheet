![latex_logo](https://user-images.githubusercontent.com/82369153/216924875-a95e02b0-020e-4169-99c0-ceb1107c54ac.png)
<div align="center">This repo is meant to be a useful non-comprehensive LaTeX Cheat Sheet that you will use while writing a LaTeX document.<br>
For everything alse go to the dedicated <a href="https://en.wikibooks.org/wiki/LaTeX">LaTeX Wikibook page</a> or <a href="https://tex.stackexchange.com/">StackExchange page</a>
</div>

---

**Table of contents**
- [Figure](#figure)
    + [Single figure](#single-figure)
    + [Multiple sub figures](#multiple-sub-figures)
      - [1x2](#1x2)
      - [2x2](#2x2)
- [Table](#table)
    + [Simple table](#simple-table)
    + [Complex table](#complex-table)
- [Math](#math)
    + [How to split math equation on multiple lines](#how-to-split-math-equation-on-multiple-lines)
- [Useful misc arguments](#useful-misc-arguments)
  * [How to properly cite an arXiv contribution on IEEE](#how-to-properly-cite-an-arxiv-contribution-on-ieee)
  * [How to highlight text for a paper review](#how-to-highlight-text-for-a-paper-review)
    + [Bypass citation](#bypass-citation)
    + [Bypass reference](#bypass-reference)

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

### How to split math equation on multiple lines
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

# Useful misc arguments
## How to properly cite an arXiv contribution on IEEE
If you have just started your adventure in the research field there is a high probabily that you have already encountered [arXiv](https://arxiv.org/). [arXiv](https://arxiv.org/) is a free distribution service and an open-access archive scholarly articles, although you can expoert directly the Bibtex formatted citation you need to properly cite the article by adding a the arXiv identifier to the note of the citation.
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

## How to highlight text for a paper review
During a paper review will be requested to highlight all the changes. A LaTeX student will be prone to to use the classic ```\textcolor{color}{text}``` command from ```\usepackage{xcolor}``` package but it will create such a monster document with an infinite repetition of ```\textcolor``` command. Also, if we need to deliver two version of the same document, e.g., one with changes highlithed and one without, will make the job tedious and endless.
One possible solution is to use the ```\usepackage{soul} ``` package:
With ```soul``` we can highlight text lightning fast with ```\hl{text to highlight}``` command, when we will not need the highlights just put the package into comment with ```%\usepackage{soul}``` and all the highlights will disappear without generating errors or warnings.
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
