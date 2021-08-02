R Markdown document is supported with the following features:

* Chunk highlighting
* Chunk navigation commands (Select current chunk, go to previous/next chunks, etc.)
* Chunk execution commands (Run current chunk, run above/below chunks, etc.)
* Rmd render commands (Knit, Knit to PDF/HTML/All)
* Live preview rmd (as html)

## Editing R Markdown documents

![Kapture 2020-10-28 at 22 25 08](https://user-images.githubusercontent.com/4662568/97449414-99a7b780-196c-11eb-9d2e-2c8eb5804d54.gif)

## Live rendering R Markdown documents

You can live preview R Markdown documents by pressing the "Open Preview to Side" button when focused on a R Markdown document. 



You can also preview a document by right-clicking it in the explorer and selecting preview.

You can also run the following code and a browser viewer will open with live rendering of the R Markdown document.

```r
rmarkdown::run("your-rmd-document.Rmd")
```
