## vscode-R

Install
[vscode-R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r) in VS
Code by searching `ikuyadeu.r` in extension marketplace.

If your R installation is from [CRAN](http://cran.r-project.org/mirrors.html),
then the default settings should work out of the box. Otherwise, you may have to
change `r.rterm.mac` to the path to your R executable, which will be executed on
command `Create R Terminal`.

## languageserver

[languageserver](https://github.com/REditorSupport/languageserver) is an
implementation of the
[Language Server Protocol](https://microsoft.github.io/language-server-protocol/)
for R.

Run the following commands in R.

You may install the latest stable release from CRAN:

```r
install.packages("languageserver")
```

or install the development version with the newest features:

```r
remotes::install_github("REditorSupport/languageserver")
```

You can also install the `rmarkdown` package and Pandoc rendering library to see
formatted R help pages upon [hover](#hover). Previews of function documentation
without these dependencies will show a plain page.

`rmarkdown` can be installed with:

```r
install.packages("rmarkdown")
```

Pandoc is
[automatically installed](https://alexd106.github.io/intro2R/install_rmarkdown.html)
if you have RStudio on your machine. See the official installation guide
[here](https://pandoc.org/installing.html) if you do not have RStudio.

## radian

[radian](https://github.com/randy3k/radian) is highly recommended as the R
terminal for interactive use. It requires Python which should be available on
macOS out of the box.

```bash
pip install -U radian
```

You may run `which radian` to see where your `radian` executable is located
(typically, `/usr/local/bin/radian`).

Then the following VS Code settings should be updated to properly use radian as
the default terminal.

```json
{
  "r.bracketedPaste": true,
  "r.rterm.mac": "/usr/local/bin/radian"
}
```

## VSCode-R-Debugger

[VSCode-R-Debugger](https://marketplace.visualstudio.com/items?itemName=RDebugger.r-debugger)
is a VS Code extension that implements R debugging capabilities. It depends on
[vscDebugger](https://github.com/ManuelHentschel/vscDebugger).

1. Install VSCode-R-Debugger extension in VS Code.
2. Install vscDebugger package via

```r
remotes::install_github("ManuelHentschel/vscDebugger")
```

## httpgd

[httpgd](https://github.com/nx10/httpgd) is an R package to provide a graphics
device that asynchronously serves SVG graphics via HTTP and WebSockets. It
enables the plot viewer based on httpgd in VS Code.

1. Install `httpgd` from CRAN

   ```r
   install.packages("httpgd")
   ```

2. Enable `r.plot.useHttpgd` in VS Code settings.
