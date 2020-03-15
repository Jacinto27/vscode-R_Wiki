# 1. vscode-R

Install [vscode-R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r) in VSCode by searching `ikuyadeu.r` in extension market place.

If your R installation is from [CRAN](http://cran.r-project.org/mirrors.html) with default installation settings, especially **Save version number in registry** is enabled as the following image shows:

<img width="500" alt="image" src="https://user-images.githubusercontent.com/4662568/76700772-ca94ee00-66f5-11ea-97bc-f89afeaf1bd3.png">

then the default settings should work out of the box. Otherwise, you may have to change `r.rterm.windows` to the path to your R executable, which will be executed on command `Create R Terminal`.

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

or install the development version with the newest features:

```r
remotes::install_github("REditorSupport/languageserver")
```

which requires [Rtools](https://cran.r-project.org/bin/windows/Rtools/) to build.

# 3. vscode-r-lsp

Install [vscode-r-lsp](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r-lsp) in VSCode by searching `reditorsupport.r-lsp` in extension market place.

If the R installation is from [CRAN](http://cran.r-project.org/mirrors.html) as decribed in the first section, then the default settings should work out of the box. Otherwise, you may have to change `r.lsp.path` to the path to your R executable, which will be executed to start the R Language Server as a background process.

# 4. radian

[radian](https://github.com/randy3k/radian) is highly recommended as the R terminal for interactive use.

Since radian is built with python, we need to install python first. Note that radian does not work with the python distributed by Microsoft Store ([radian#120](https://github.com/randy3k/radian/issues/120)), we need to install the official version. Go to [Python Releases for Windows](https://www.python.org/downloads/windows/) and download the latest executable installer, e.g. [Windows x86-64 executable installer](https://www.python.org/ftp/python/3.7.7/python-3.7.7-amd64.exe).

<img width="670" alt="image" src="https://user-images.githubusercontent.com/4662568/76701870-219fc080-6700-11ea-8487-18ab880dab88.png">

Make sure **Add Python 3.x to PATH** is selected.

Then start a command prompt or Windows PowerShell terminal and type in the following command to install `radian` via `pip`:

```sh
pip install -U radian
```

To locate the path to `radian.exe`, run the following command:

```sh
where.exe radian
```

Then the following VSCode settings should be updated to properly use radian as the default terminal. If your `radian` is installed only for `user`:

```json
{
  "r.bracketedPaste": true,
  "r.rterm.windows": "C:\\Users\\user\\AppData\\Local\\Programs\\Python\\Python37\\Scripts\\radian.exe"
}
```
