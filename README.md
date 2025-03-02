This project demo is published at:
https://phiggins.quarto.pub/quarto-live-book

To make this project work, I 

1. opened the project as a
New Project/Quarto book

2. Went to the Terminal tab, then entered 'quarto add r-wasm/quarto-live'
to add the right extension

3. Then agreed to trust the authors (Yes)

4. Then edited the _quarto.yml file to look like this:

project:<br>
&nbsp;&nbsp;type: book <br>

book: <br>
&nbsp;&nbsp;title: "quarto-live-book" <br>
&nbsp;&nbsp;author: "PDRH" <br>
&nbsp;&nbsp;date: "3/1/2025" <br>
&nbsp;&nbsp;chapters: <br>
&nbsp;&nbsp;&nbsp;&nbsp;- index.qmd <br>
&nbsp;&nbsp;&nbsp;&nbsp;- intro.qmd <br>
&nbsp;&nbsp;&nbsp;&nbsp;- summary.qmd <br>
&nbsp;&nbsp;&nbsp;&nbsp;- references.qmd <br>

bibliography: references.bib <br>

format: live-html <br>
engine: knitr <br>
editor: visual <br>

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

This sets the format to that chapter to live-html, and loads 3 packages (you can change these to whatever packages you might need in that chapter).

The last bit, outside of the yaml header, sets up the knitr engine for R

6. Then for each code chunk,
if I want it to be static - leave the chunk label as something like this:

{r chunk-name}

If I want it to be a LIVE code chunk, I need to start the code chunk with {webr}
like this:

{webr chunk-name2}


7. Then I edit each qmd file, and render it to make sure it looks like what I expect.

8. Then to publish this to the quarto-pub website,
I go back to Terminal, to the directory for this project,
then enter `quarto publish` and Enter
<br>
I will be asked whether to publish to my usual quarto-pub domain
(say yes, Enter)
and it renders the whole book for me (after asking me to confirm authorization to quarto-pubs)
to quarto-pubs
<br>
<br>

There is a lot more help on how to build quarto books here - <br> https://quarto.org/docs/reference/projects/books.html
<br>
<br>
And even more help on options for quarto-live (and exercises) here - <br> https://r-wasm.github.io/quarto-live/
