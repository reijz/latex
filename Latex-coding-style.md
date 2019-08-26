---
title: Latex Coding Style
author: Jiheng Zhang
date:   2016-02-08 16:15:05 +0800
tags: [latex]
---

# Latex Coding Style

Often in time, I find many latex source files in a mess, making editing an excruciating experience. This is not necessarily the case if we can tide up the source file. Here are some coding style I suggest, that will make the source code neat, readable and not so painful to do editing. Since we use git, it also makes `diff` easy.

## Math displays

The numbered equations should be coded like

```latex
\begin{equation}
  \label{eq:energy-mass}
  E = MC^2
\end{equation}
```

Please avoid using `\[...\]`. There are convenient shortcuts in a good editor (e.g., emacs) to auto type the `begin/end` environments. Also, the content in the environment should be indented (by two spaces).

## Labeling

In order that equations/sections/theorems/etc. to be cited later without too much pain, a neat labelling system is necessary. A label should be like `{type:content}` where `type` could be "eq", "thm", "cond", etc. and `content` should suggest the content of the labeled object. For example, the above equation is labeled as `{eq:energy-mass}`.

## Text

**One sentence or a group of sentences on the same point per line**. Do not wrap the whole paragraph in one line. There are three reasons for this: 

1. It helps to organize your thoughts. 
2. We use git for version control. The `diff` is implemented line by line. Writing in this way helps to see what are changed in different versions.
3. Backward search (from pdf to latex) is done by "lines". Such an organization help you go back to exact the line you want to edit in the latex from the location in the pdf file.  

## Tables and Figures

All Tables and Figures should be created using [pgf plot](http://pgfplots.sourceforge.net). Here are some [example](http://pgfplots.net/tikz/examples/) of using this latex package. The advantage is that no more saving to pdf/picture. 

Numerical experiment (done by any tools like Python, Julia, etc.) can output to a file. And latex (via pgfplot package) can directly read this file to plot a figure or create a table. 

## Annotation

Commenting out a large chunk of code is strictly prohibited. If we are not sure whether it will be needed later, **highlight** it instead of commenting it out. Over the iteration, we either delete it or modify it. 

Comment `%` can **ONLY** be used in the annotation way. For example, 

```latex
\newcommand{\fl}[1]{\lfloor{#1}\rfloor} % floor of a number

...

% ---- Literature review ---- 

...

% ---- challenge 2 ---- 
...

% ---- what we do ----
...

% ---- contributions ----

```

The following is a nice way to send message to coauthors

```latex
% >>> author 1: This is an issue to be solved
% >>>> author 2: I made a few edits. See if that suffices.
```

**Never use** 

```latex
\iffalse
...
\fi
```

## Macros

Here are some macros I defined for convenience. 

```latex
% some macro for typing
\newcommand{\R}{\mathbb{R}} % real numbers
\newcommand{\Q}{\mathbb{Q}} % rational numbers
\newcommand{\Z}{\mathbb{Z}} % integer numbers
\newcommand{\N}{\mathbb{N}} % natural numbers

\newcommand{\fl}[1]{\lfloor{#1}\rfloor} % floor of a number
\newcommand{\cl}[1]{\lceil{#1}\rceil} % ceiling of a number
\newcommand{\norm}[2]{\|{#2}\|_{#1}} % norm

% for highlighting changes
\usepackage[normalem]{ulem}
\newcommand{\delete}[1]{\textcolor{red}{\sout{#1}}} % delete
\newcommand{\ins}[1]{\textcolor{red}{\v{}{#1}}} % insert
\newcommand{\replace}[2]{\textcolor{red}{\sout{#1}} \textcolor{blue}{{#2}}} % replace #1 with #2
\newcommand{\emp}[1]{\textcolor{red}{#1}} % emphasize
\newcommand{\cmt}[2]{\textcolor{blue}{({#1}: {#2})}} % comments
```

However, I do not suggest to define `\lm` for `\lambda`. It does not worth the trouble. Also, if using a good editor (e.g., emacs), frequently used code such as `\lambda` are done by convenient shortcuts. 

