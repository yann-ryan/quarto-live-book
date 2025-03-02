This project demo is published at:
https://phiggins.quarto.pub/quarto-live-book

To make this project work, I 

1. opened the project as a
New Project/Quarto book

2. Went to the Terminal tab, then entered 'quarto add r-wasm/quarto-live'
to add the right extension

3. Then agreed to trust the authors (Yes)

4. Then edited the -quarto.yml file to look like this:

project:
&nbsp;&nbsp;type: book

book:
&nbsp;&nbsp;title: "quarto-live-book"
&nbsp;&nbsp;author: "PDRH"
&nbsp;&nbsp;date: "3/1/2025"
&nbsp;&nbsp;chapters:
&nbsp;&nbsp;&nbsp;&nbsp;- index.qmd
&nbsp;&nbsp;&nbsp;&nbsp;- intro.qmd
&nbsp;&nbsp;&nbsp;&nbsp;- summary.qmd
&nbsp;&nbsp;&nbsp;&nbsp;- references.qmd

bibliography: references.bib

format: live-html
engine: knitr
editor: visual

5. Then at the top of each of the default chapters
(index.qmd, intro.qmd, summary.qmd) inserted the following at the top of each file:

`---` <br>
format: live-html <br>
webr: <br>
&nbsp;&nbsp;packages: <br>
&nbsp;&nbsp;&nbsp;&nbsp;- dplyr <br>
&nbsp;&nbsp;&nbsp;&nbsp;- palmerpenguins <br>
&nbsp;&nbsp;&nbsp;&nbsp;- ggplot2 <br>
`---` <br>

`{{< include ./_extensions/r-wasm/live/_knitr.qmd >}}`

This sets the format to that chapter to live-html, and loads 3 packages.

The bit outside of the yaml header sets up the knitr engine for R

6. Then for each code chunk,
if I want it to be static - leave as something like this:

```{r}
1 + 1
```

If I want it to be a LIVE code chunk, I need to start with {webr}
like this:

```{webr}
1 + 1
```
