# 1. vscode-R

Install [vscode-R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r) in VSCode by searching `ikuyadeu.r` in extension market place.

If the R installation is from [CRAN](http://cran.r-project.org/mirrors.html), then the default settings should work out of the box. Otherwise, you may have to change `r.rterm.mac` to the path to your R executable, which will be executed on command `Create R Terminal`.

If you are interested in the experimental features provided by [R session watcher](https://github.com/Ikuyadeu/vscode-R/wiki/R-Session-watcher), you may enable it in the VSCode settings:

```json
{
  "r.sessionWatcher": true
}
```

# 2. languageserver

[languageserver](https://github.com/REditorSupport/languageserver) is an implementation of the [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) for R.

Run the following commands in R.

You may install the latest stable release from CRAN:

```r
install.packages("languageserver")
``` 

or install the development version with newest features:

```r
remotes::install_github("REditorSupport/languageserver")
```

# 3. vscode-r-lsp

Install [vscode-r-lsp](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r-lsp) in VSCode by searching `reditorsupport.r-lsp` in extension market place.

If the R installation is from [CRAN](http://cran.r-project.org/mirrors.html), then the default settings should work out of the box. Otherwise, you may have to change `r.lsp.path` to the path to your R executable, which will be executed to start the R Language Server as a background process.

# 4. radian

[radian](https://github.com/randy3k/radian) is highly recommended as the R terminal for interactive use. It requires python which should be available on macOS out of the box.

```bash
pip install -U radian
```

You may run `which radian` to see where your `radian` executable is located (typically, `/usr/local/bin/radian`).

Then the following VSCode settings should be updated to properly use radian as the default terminal.

```json
{
  "r.bracketedPaste": true,
  "r.rterm.mac": "/usr/local/bin/radian"
}
```
