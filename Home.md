vscode-R is the R Extension for Visual Studio Code.

## Features

* Create R Integrated Terminal
* Run Source/Selected Line
* Run `nrow`, `length`, `head`, `thead`, `names` functions (`Ctrl` + `1`, `2`, `3`, `4`, `5`)
* Run code in terminal containing existing R session, for example over SSH (`Run Selection/Line in Active Terminal`)
* Run all commands in terminal containing existing R session (enable config `r.alwaysUseActiveTerminal`)
* Extended Syntax (R, R Markdown, R Documentation)
* Create `.gitignore` based on [R.gitignore](https://github.com/github/gitignore/raw/master/R.gitignore)
* Data frame viewer and Environment viewer(`Preview Data frame` or `Preview Environment`)
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

* `r.rterm.windows`: set to R.exe path for Windows
* `r.rterm.mac`: set to R term's path for Mac OS X
* `r.rterm.linux`: set to R term's path for Linux
* `r.rpath.lsp`: set to R.exe path for Language Server Protocol
* `r.rterm.option`: R command line options (i.e: --vanilla)
* `r.source.encoding`: An optional encoding to pass to R when executing the file
* `r.source.focus`: Keeping focus when running (editor or terminal)
* `r.alwaysUseActiveTerminal`: Use active terminal for all commands, rather than creating a new R terminal
* `r.bracketedPaste`: For consoles supporting bracketed paste mode (such as Radian)
* `r.sessionWatcher`: Enable R session watcher (experimental)
