## vscode-R

Install [vscode-R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r) in VS Code by searching `ikuyadeu.r` in extension marketplace.

If your R installation is from [CRAN](http://cran.r-project.org/mirrors.html), then the default settings should work out of the box. Otherwise, you may have to change `r.rterm.linux` to the path to your R executable, which will be executed on command `Create R Terminal`.

If you are interested in the experimental features provided by [R session watcher](https://github.com/Ikuyadeu/vscode-R/wiki/R-Session-watcher), you may enable it in the VS Code settings:

```json
{
  "r.sessionWatcher": true
}
```

## languageserver

[languageserver](https://github.com/REditorSupport/languageserver) is an implementation of the [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) for R.

Run the following commands in R.

You may install the latest stable release from CRAN:

```r
install.packages("languageserver")
``` 

or install the development version with the newest features:

```r
remotes::install_github("REditorSupport/languageserver")
```

## vscode-r-lsp

Install [vscode-r-lsp](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r-lsp) in VS Code by searching `reditorsupport.r-lsp` in extension marketplace.

If the R installation is from [CRAN](http://cran.r-project.org/mirrors.html), then the default settings should work out of the box. Otherwise, you may have to change `r.rpath.*` to the path to your R executable, which will be executed to start the R Language Server as a background process.

## radian

[radian](https://github.com/randy3k/radian) is highly recommended as the R terminal for interactive use. It requires Python which should be available on most Linux distributions out of the box.

To install it globally:

```bash
pip install -U radian
```

Or if you don't have root privilege, you may want to install it only for yourself:

```bash
pip install --user radian
```

You may run `which radian` to see where your `radian` executable is located.

Then the following VS Code settings should be updated to properly use radian as the default terminal. If your `radian` is installed only for `user`:

```json
{
  "r.bracketedPaste": true,
  "r.rterm.linux": "/home/user/.local/bin/radian"
}
```

## VSCode-R-Debugger

[VSCode-R-Debugger](https://marketplace.visualstudio.com/items?itemName=RDebugger.r-debugger) is a VS Code extension that implements R debugging capabilities. It depends on [vscDebugger](https://github.com/ManuelHentschel/vscDebugger).

1. Install VSCode-R-Debugger extension in VS Code.
2. Install vscDebugger package via

```r
remotes::install_github("ManuelHentschel/vscDebugger")
```

## httpgd

[httpgd](https://github.com/nx10/httpgd) is an R package to provide a graphics device that asynchronously serves SVG graphics via HTTP and WebSockets. It enables the plot viewer based on httpgd in VS Code.

1. Install `httpgd` from CRAN

```r
install.packages("httpgd")
```

2. Enabled httpgd-based plot viewer by inserting the following option in your `~/.Rprofile`:

```r
options(vsc.use_httpgd = TRUE)
```