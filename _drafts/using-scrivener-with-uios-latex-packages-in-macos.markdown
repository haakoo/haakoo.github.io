---
layout: post
title: Using Scrivener with UiO's LaTeX packages in macOS
tags:
- english
- latex
- scrivener
- uio
- macos
---

I recently help my other half set up Scrivener to export her master thesis to LaTeX, so she could use the front page template from the University of Oslo to create a nice looking PDF.

The University of Oslo have both a Microsoft Word and a LaTeX [template for master thesis'](https://www.ub.uio.no/skrive-publisere/masteroppgaver/maler/). Here I'll describe how I got the LaTeX template to work with Scrivener's LaTeX export in macOS.



## Scrivener

If you don't already know [Scrivener](https://www.literatureandlatte.com/scrivener.php), here is a short introduction. Scrivener is a tool for writing and organising text. It started out as a tool for authors to use when writing novels, short stories and other long form texts. The most powerful functionality in Scrivener is how easy it is to rearrange and organise your text. Add in the ability to add lots of metadata at different levels and you have a very powerful writing tool. A lot of people in academia have found Scrivener to be a very good fit for writing a master thesis or organise a PhD dissertation. After you've written your text, you need to *export it* from Scrivener into a format fit for publication. Scrivener call this step *compiling the document* using the `Compile` feature. There are several output options, like Microsoft Word document, PDF, HTML, several e-book formats and more. A very versatile option is the ability to export using MultiMarkdown formatting, either to MMD, HTML, Rich Text or LaTeX.



## The three steps

The process was surprisingly simple and can be summarised as the following three steps:

1. Install MacTex
2. Download and extract the template
3. Set up Scrivener to compile to LaTeX

When all this i done, you can easily compile your scrivener document to LaTeX source, and use `pdflatex` to create a very nice looking PDF without any manual editing of LaTeX source.



### 1. Installing MacTex

To be able to compile the exported LaTeX source to a finished PDF you need to install [MacTex](https://www.tug.org/mactex/) (or an equivalent). This is fairly straight forward using the installer found on the MacTex page. After you've successfully installed MacTex you can run a few new commands in the Terminal. The one command you'll need is `pdflatex`. If you use BibTeX for references, you'll also need the `bibtex` command.



### 2. Download and extract the template

The package for the UiO master front page is called *duomasterforside*, and it has a good [manual](http://dag.at.ifi.uio.no/public/doc/duomasterforside-guide.pdf). You'll need to download the template files from [here](http://dag.at.ifi.uio.no/public/download/duoforside.zip). Extract the zip file in you Download folder, on your Desktop or wherever you want to. The next step is to put the files where they belong.

I looked around the web to find a guide for installing local packages in macOS, and found one over at *Tex - LaTeX Stack Exchange* and the answer to the question [How to have local package override default package](http://tex.stackexchange.com/a/8359/10647). It turns out it is very easy to install local LaTeX packages for your own user. All you have to do is add the LaTeX package to the folder `~/Library/texmf/tex/LaTeX`. To do this open a new Finder window and press `Cmd (⌘) + Shift (⇧) + G` to open the *Go to the folder:* dialog. Then type in `~/Library`and hit enter.

![macOS Finder with the Go to the folder: dialog](/assets/images2/2017/05/Finder-with-the-Go-to-the-folder-dialog.png)

Find the `texmf` folder or create it, if it is missing. Then create the `tex` folder inside that again. In the `tex` folder you create a `latex` folder and a `doc` folder. Inside both of these you create a `duomasterforside` folder, this is where you'll put the package files.

From the extracted files you copy or move all the files[^1] in the main folder (not the `doc` folder) into the `~/Library/texmf/tex/latex/duomasterforside` folder.

![macOS Finder showing the content of the ~/Library/texmf/tex/latex/duomasterforside folder](/assets/images2/2017/05/Finder-with-content-of-latex-duomasterforside-folder.png)

Then you copy or move the remaining file[^2] in the extracted `doc` folder into `~/Library/texmf/tex/doc/duomasterforside`

![macOS Finder showing the content of the ~/Library/texmf/tex/doc/duomasterforside folder](/assets/images2/2017/05/Finder-with-content-of-doc-duomasterforside-folder.png)



## 3. Set up Scrivener to compile to LaTeX
<span style="background-color:red">???</span>

### Compile options
Lots of compile options and screen shots and inserted LaTeX code.

#### Header
```latex
\documentclass[a4paper,UKenglish,12pt]{ifimaster}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc,url}
\urlstyle{sf}
\usepackage{babel,textcomp,csquotes,duomasterforside,varioref,graphicx}
\usepackage[backend=biber,style=numeric-comp]{biblatex}
\usepackage{parskip}
\usepackage[pdfstartview={FitV},linktoc=all]{hyperref}
```

#### Begin Document
```latex
\title{\mytitle}
\author{\myauthor}

\newenvironment{unnumbered}
   {\global\chardef\keeplevel=\value{secnumdepth}
    \setcounter{secnumdepth}{-1}}
   {\setcounter{secnumdepth}{\keeplevel}}

\begin{document}
\duoforside[program={Linguistics},
  dept={Department of Linguistics and Scandinavian Studies},
  fac={Faculty of Humanities}]

```


### Extra *"texts"* in the project
So we can compile the document to LaTeX source from Scrivener, but not everything is as we would like. The page numbering for front matter is the same as the main text, not ideal. We're missing a table of contents and the back matter and appendices are not like we'd like them.

What I did to fix all this was add several extra *"texts"* to the project in Scrivener.
<span style="background-color:red">???</span>


### Scrivener compile settings
<span style="background-color:red">???</span>

#### Contents
<span style="background-color:red">???</span>

#### Separators
<span style="background-color:red">???</span>

#### Formatting
<span style="background-color:red">???</span>

#### Transformations
<span style="background-color:red">???</span>

#### LaTeX Options
<span style="background-color:red">???</span>

#### Meta-Data
<span style="background-color:red">???</span>


````
Title = <$projecttitle>
Author = <$author>
Base Header Level = 2
```

## Extras

Here follows a couple of extra hints and tricks.


### Modify the document formatting

You might have noticed that I've added a couple of tweeks to the document. Mainly this is done by using the [`ifimaster`](http://dag.at.ifi.uio.no/public/download/ifimaster.cls) package, which have lots of subtle changes to make the formatting more European like. To install this, follow the recipe for `duomasterforside`, but save the `.cls` file into `~/Library/texmf/tex/latex/ifimaster` folder, there is no documentation for this package, but there is an [example](http://dag.at.ifi.uio.no/public/download/mymaster.tex).

In addition to using a different class, I changed the normal indentation of paragraphs to a vertical space and removed the numbering for the front and back matter.

Changing the indentation for paragraphs is so common (and tricky to get right) that there is a package for it, namely the [`parskip`](http://ctan.org/pkg/parskip) package. This is what I did by adding `\usepackage{parskip}` to the preamble in the *LaTeX Options* *Header*-section in Scrivener.

Removing the numbering in the front and back matter was a little more fiddly and done creating a new environment that surround everything in the front and back matter. I found the solution to this in the answer to the question [Make \chapter* same as unnumbered \chapter (using memoir) ?](http://tex.stackexchange.com/a/17051/10647). By adding the environment declaration in the preamble and then using `\begin{unnumbered}` before and `\end{unnumbered}` after the front and back matter the `\chapters` become unnumbered.

There is even more information on the use of LaTeX at UiO over at the Institute for Informatics LaTeX pages [Informasjon om LaTeX med venner](https://www.mn.uio.no/ifi/tjenester/it/hjelp/latex/) (only in Norwegian). An other very good resource for general LaTeX is the [LaTeX book](https://en.wikibooks.org/wiki/LaTeX) over at Wikibooks.

### Using BibTex for references
This is smart...

<span style="background-color:red">???</span>

### Adding right click to compile in macOS

Even though it all works, it is a bit cumbersome to open Terminal to compile the document and create a PDF file. I decided to find a way to add an option to the right click menu in Finder to compile the document. 

<span style="background-color:red">How do I do this?</span>




[^1]: The files: **DUO\_UiO\_segl.eps.bb**, **DUO\_UiO\_segl.png**, **duoforside.tex**, **DUO\_UiO\_segl.eps.gz**, **duoforside.sty** and **duomasterforside.sty**
[^2]: The file: **duomasterforside-guide.pdf**