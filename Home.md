vscode-R is the R Extension for [Visual Studio Code](https://code.visualstudio.com/). The extension is mainly focused on providing user interactivity between VSCode and R sessions. To make VSCode more powerful in R scripting, it is highly recommended to also install the R language server ([languageserver](https://github.com/REditorSupport/languageserver) and [vscode-r-lsp](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r-lsp)).

Visit the links on the right for more information.

This project won't be successful without contributions, especially the current and past key collaborators:

* Kun Ren ([@renkun-ken](https://github.com/renkun-ken))
* Andrew Craig ([@andycraig](https://github.com/andycraig))
* Thomas Brittain ([@Ladvien](https://github.com/Ladvien))
* Miles McBain ([@MilesMcBain](https://github.com/MilesMcBain))
* Manuel Hentschel ([@ManuelHentschel](https://github.com/ManuelHentschel))

## Features

* Create R Integrated Terminal
* Run Source/Selected Line
* Run functions:
  * `nrow` (`Show number of rows for selected object`)
  * `length` (`Show length for a selected object`)
  * `head` (`Show first part of a selected object`)
  * `thead` (`Show first part of a selected object (transposed)`)
  * `names` (`Show names for a selected object`)
* Run all commands in active terminal containing existing R session (enable config `r.alwaysUseActiveTerminal`)
* Extended Syntax (R, R Markdown, R Documentation)
* Create `.gitignore` based on [R.gitignore](https://github.com/github/gitignore/raw/master/R.gitignore)
* Data frame viewer and Environment viewer (`Preview Data frame` or `Preview Environment`)
* Snippets
* Package development shortcuts (`Load All`, `Test Package`, `Install Package`, `Build Package` and `Document`)
* Bind keys to custom R commands using command runner functions (`r.runCommand`, `r.runCommandWithEditorPath`, `r.runCommandWithSelectionOrWord`)
* R Session Watcher to interact with R sessions
  * Watch any R session
  * Show value of session symbols on hover
  * Provide completion for session symbols
  * `View()` any objects including data frames and list objects
  * Show plot output on update and plot history
  * Show htmlwidgets, documentation and shiny apps in WebView

## Extension Settings

* `r.rterm.windows`: R.exe path for windows.
* `r.rterm.mac`: R path for Mac OS X.
* `r.rterm.linux`: R path for Linux.
* `r.rterm.option`: R command line options.
* `r.source.encoding`: An optional encoding to pass to R when executing the file, i.e. `source(FILE, encoding=ENCODING)`.
* `r.source.focus`: Keeping focus when running.
* `r.alwaysUseActiveTerminal`: Use active terminal for all commands, rather than creating a new R terminal.
* `r.bracketedPaste`: Use bracketed paste mode when sending code to console. Enable for Radian console.
* `r.sessionWatcher`: Enable R session watcher (experimental). Restart required to take effect.
