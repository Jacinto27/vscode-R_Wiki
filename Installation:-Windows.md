## vscode-R

Install [vscode-R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r) in VS Code by searching `ikuyadeu.r` in extension marketplace.

If your R installation is from [CRAN](http://cran.r-project.org/mirrors.html) with default installation settings, especially **Save version number in registry** is enabled as the following image shows:

<img width="500" alt="image" src="https://user-images.githubusercontent.com/4662568/76700772-ca94ee00-66f5-11ea-97bc-f89afeaf1bd3.png">

Then the default settings should work out of the box. Otherwise, you may have to change `r.rterm.windows` to the path to your R executable, which will be executed on command `Create R Terminal`.

If you are interested in the experimental features provided by [R session watcher](https://github.com/REditorSupport/vscode-R/wiki/R-Session-watcher), you may enable it in the VS Code settings:

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

which requires [Rtools](https://cran.r-project.org/bin/windows/Rtools/) to build.

## vscode-r-lsp

Install [vscode-r-lsp](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r-lsp) in VSC ode by searching `reditorsupport.r-lsp` in extension marketplace.

If the R installation is from [CRAN](http://cran.r-project.org/mirrors.html) as described in the first section, then the default settings should work out of the box. Otherwise, you may have to change `r.lsp.path` to the path to your R executable, which will be executed to start the R Language Server as a background process.

## radian

[radian](https://github.com/randy3k/radian) is highly recommended as the R terminal for interactive use.

Since radian is built with python, we need to install python first. Note that radian does not work with the python distributed by Microsoft Store ([radian#120](https://github.com/randy3k/radian/issues/120)) before v0.5.4, we need to install the official version. Go to [Python Releases for Windows](https://www.python.org/downloads/windows/) and download the latest executable installer, e.g. [Windows x86-64 executable installer](https://www.python.org/ftp/python/3.7.7/python-3.7.7-amd64.exe).

<img width="670" alt="image" src="https://user-images.githubusercontent.com/4662568/76701870-219fc080-6700-11ea-8487-18ab880dab88.png">

Make sure **Add Python 3.x to PATH** is selected.

Then start a command prompt or Windows PowerShell terminal and type the following command to install `radian` via `pip`:

```sh
pip install -U radian
```

To locate the path to `radian.exe`, run the following command:

```sh
where.exe radian
```

Then the following VS Code settings should be updated to properly use radian as the default terminal. Put the path to `radian.exe` in `r.rterm.windows` with all `\` replaced with `\\`. For example, if your `radian` is installed for `user`:

```json
{
  "r.bracketedPaste": true,
  "r.rterm.windows": "C:\\Users\\user\\AppData\\Local\\Programs\\Python\\Python37\\Scripts\\radian.exe"
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
