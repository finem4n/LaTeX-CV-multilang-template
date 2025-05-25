# Multi-Lingual LaTeX Modern-CV Template
## Purpose of This Project
[This is a fork of generic template](https://github.com/novoid/LaTeX-CV-template) for [LaTeX](http://en.wikipedia.org/wiki/LaTeX) documents using the [KOMA Script](http://www.komascript.de/)
class [koma-moderncvclassic](https://ctan.org/pkg/koma-moderncvclassic?lang=en).

The target audience is somebody with LaTeX-knowledge who wants to have
his/her CV in two languages. By default, this template is using
English and Polish.

The template does *not* want to contain each and every trick. It
should provide a starting point for one type of CV.

This fork shows how to apply bi-linguality to any CV template.

## Requirements
This template uses pdflatex and [GNU make.](http://www.gnu.org/s/make/) You should be familiar with
compiling LaTeX documents by yourself. If you are new to LaTeX please
get basic knowledge from tutorial pages such as [this one](http://LaTeX.TUGraz.at).

Since switching languages makes use of symbolic links, *this template
does not work on Windows machines without further adaptations*.

Please ensure that all required LaTeX packages are installed, especially `babel.sty` and `optional.sty`.

## What Makes This Template Special?

By using this template, you just have to maintain your CV in one
single LaTeX file and get two different PDF files for two different
languages.

## How to Start?

You will need to adapt the following things:

1. Edit the `Makefile` and set the `FIRSTNAME`, `LASTNAME` and `PDFVIEWER` variables.
2. Add those lines to your main.tex before `\begin{document}`:
```tex
\input{language}
\newcommand{\en}[1]{\opt{en}{#1}}
\newcommand{\pl}[1]{\opt{pl}{#1}}
```

And after `\begin{document}`:
```tex
\section{\pl{Przykład}\en{Example}}

\en{This text will be visible in English CV only}
\pl{Ten tekst będzie widoczny tylko w polskim CV}

Text outside of \\en{} and \\pl{} will be visible in both CV versions.

Tekst poza \\en{} i \\pl{} będzie widoczny w obu wersjach CV.
```

3. Generate the result PDF files:
   - `make -C src pdfen` for the English CV only
   - `make -C src pdfpl` for the Polish CV only
   - `make -C src all` for both CVs

You can learn about the other helpful make targets by invoking:

```sh
make -C src help
```

## TODOs
- [ ] Check why `\usepackage[polish]{babel}` doesn't work on my system (Is babel package divide into smaller packages?).
