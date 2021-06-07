# LaTeX

“LaTeX, which is pronounced «Lah-tech» or «Lay-tech», is a document preparation system for high-quality typesetting. It is most often used for medium-to-large technical or scientific documents but it can be used for almost any form of publishing.”

[What is the difference between TeX and LaTeX?](https://tex.stackexchange.com/questions/49/what-is-the-difference-between-tex-and-latex)

## Get LaTeX

* [MacOS](http://www.tug.org/mactex/) \(Required\)
* Windows
  * [MiKTeX ](http://miktex.org/)\(Required\)
  * [TexMaker](http://www.xm1math.net/texmaker/download.html#windows)
  * [proTeXt](http://www.tug.org/protext/)
  * [TeX Live](http://www.tug.org/texlive)
* Linux
  * [Tex Live ](http://www.tug.org/texlive)\(Required\)

[Source](https://www.latex-project.org/get/)

## Manually Package Management

On \*nix systems `tlmgr` can be used to install and update packages from the command line.

### Install Package

If you're on macOS and have opted for the smaller `BasicTeX` instead of the full install you won't have access to the `\author` or `\affil` commands provided by the `authblk` package. You'll need to install it manually.

The [CTAN page](https://ctan.org/pkg/authblk) for `authblk` states “The pack­age is part of the [preprint](https://ctan.org/pkg/preprint) bun­dle.”.

To get access to `authblk` we need to install the `preprint` bundle via: `sudo tlmgr install preprint`

### Update Packages

Executing `sudo tlmgr update –list` will display which packages need to be updated.

Executing `sudo tlmgr update –all` will actually update them.

## Compiling Tex to PDF

### MacOS, Linux and Windows

`cd` Into the directory containing your .tex and .bib files and run:

1. `pdflatex whitepaper.tex`

To build your Bibliography run:

1. `pdflatex whitepaper.tex`
2. `bibtex whitepaper.aux`
3. `pdflatex whitepaper.tex`

To build your Glossary run:

1. `pdflatex whitepaper.tex`
2. `makeglossaries whitepaper` 
3. `pdflatex whitepaper.tex`

### Shit You Might Encounter While Compiling

* When using the `glossaries` package the `\printglossaries` command wont print your Glossary if you've suppressed page numbers with `\pagenumbering{gobble}`

## Editors

* [gummi](https://github.com/alexandervdm/gummi) “Simple LaTeX editor” \[Linux & Windows\]

## Referencing

From September 2017, Abertay adopted the Cite Them Right version of Harvard

When referencing a website the references page entry should look like:

```text
  National Literacy Trust (2011) Policy. Available at: http://www.literacytrust.org.uk/policy
  (Accessed: 7 January 2011).
```

The in-text citation should look like:

```text
  (National Literacy Trust, 2011)
```

The `natbib` package can be used to achieve this referencing style. The following should be in your preamble:

```text
  \usepackage{natbib}
  \setcitestyle{aysep={,}}
```

The following should be placed wherever you want your References page rendered:

```text
  \bibliographystyle{agsm}
  \bibliography{bibfile}
```

The following entry in your `.bib` file will produce the correct reference page entry:

```text
  @misc{nlt_2011,
  title={Policy},
  author={{N}ational {L}iteracy {T}rust},
  year={2011},
  Howpublished={Available at: \url{www.literacytrust.org.uk/policy}},
  Note={(Accessed: February 22nd, 2017)}
  }
```

Credit to [Rory](https://twitter.com/Sheldorr) for putting in most of the leg work on this.

## Formatting

### Tilde

```text
\newcommand\customtilderaise.17ex_hbox_scriptstyle_mathtt_sim}
```

Usage: `Cost \customtilde \$10,000`

[Source](https://tex.stackexchange.com/questions/9363/how-does-one-insert-a-backslash-or-a-tilde-into-latex/9372#9372)

### Page Breaks

> In situations like a chapter start it is advisable to end the previous chapter with a `\clearpage` to flush out all floats, but in other situations this might result fairly empty pages with only floats on them which may or may not be desired.
>
> A second difference is `\clearpage` actually always starts a new “page” while `\newpage` really only ends the current column.

[Source](https://tex.stackexchange.com/questions/45609/is-it-wrong-to-use-clearpage-instead-of-newpage)

## Templates

* Template for 4th year dissertation proposal \(two-column\) – Two column proposal template
* Template for 4th year dissertation \(one column, 1.5 line spaced with special documentation pages and title page\) – Dissertation Template with Bibliography and LoT and LoF

#### Syntax Highlighting

```text
  \usepackage{listings}
  \usepackage{color}

  \definecolor{codegreen}{rgb}{0,0.6,0}
  \definecolor{codegray}{rgb}{0.5,0.5,0.5}
  \definecolor{codepurple}{rgb}{0.58,0,0.82}
  \definecolor{backcolour}{rgb}{0.95,0.95,0.92}

  \lstdefinestyle{mystyle}{
      backgroundcolor=\color{backcolour},   
      commentstyle=\color{codegreen},
      keywordstyle=\color{magenta},
      numberstyle=\tiny\color{codegray},
      stringstyle=\color{codepurple},
      basicstyle=\footnotesize,
      breakatwhitespace=false,         
      breaklines=true,                 
      captionpos=b,                    
      keepspaces=true,                 
      numbers=left,                    
      numbersep=5pt,                  
      showspaces=false,                
      showstringspaces=false,
      showtabs=false,                  
      tabsize=2
  }
```

Then use

```text
  \begin{lstlisting}[language=Python,style=MyStyle]
      Radge code
  \end{lstlisting}
```

## Packages

### textcomp

Enables support for Text Companion fonts such as legal, currency and mathematical symbols.

```text
  \usepackage{textcomp}

  A\textrightarrow B
  10\textcelsius
  Sony\texttrademark
```

## Resources

* [tablesgenerator.com](http://www.tablesgenerator.com/) Create pretty tables and paste in auto generated Tex 
* [Tex StackExchange](https://tex.stackexchange.com/)
* [Awesome Documentation that 'just works'](https://www.sharelatex.com/learn)
* [The Comprehensive LATEX Symbol List](https://www.cs.cmu.edu/~bhudson/symbols-letter.pdf)
* [Arbitrary LaTeX Reference](http://latex.knobs-dials.com/) “Many problems in LaTeX requires some research, so I started to record my findings.”

