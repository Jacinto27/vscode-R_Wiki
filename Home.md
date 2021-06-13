vscode-R is the R Extension for [Visual Studio Code](https://code.visualstudio.com/). The extension is mainly focused on providing user interactivity between VSCode and R sessions. To make VSCode more powerful in R scripting, it is highly recommended to also install the R language server ([languageserver](https://github.com/REditorSupport/languageserver) and [vscode-r-lsp](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r-lsp)).

Visit the links on the right for more information.

This project won't be successful without contributions, especially the current and past key collaborators:

* Kun Ren ([@renkun-ken](https://github.com/renkun-ken))
* Andrew Craig ([@andycraig](https://github.com/andycraig))
* Thomas Brittain ([@Ladvien](https://github.com/Ladvien))
* Miles McBain ([@MilesMcBain](https://github.com/MilesMcBain))
* Manuel Hentschel ([@ManuelHentschel](https://github.com/ManuelHentschel))
* Elian H. Thiele-Evans ([@ElianHugh](https://github.com/ElianHugh))

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

This extension contributes the following settings:

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
* `r.rtermSendDelay`: Delay in milliseconds before sending each line to rterm (only applies if r.bracketedPaste is false)
* `r.rmarkdown.enableCodeLens`: Enable RMarkdown CodeLens, which are inline commands/buttons e.g. 'Run Chunk | Run Above' shown on the first line of each code chunk.
  <details>
    <summary>Details</summary>

  * Click the buttons to run commands.
  * Hover on the buttons to show tooltips.
  * CodeLens commands are customizable via settings UI (Rmarkdown: Code Lens commands) or settings.json `r.rmarkdown.codeLensCommands`
  </details>
* `r.rmarkdown.codeLensCommands`: Customize RMarkdown CodeLens, which are inline commands/buttons e.g. 'Run Chunk | Run Above' shown on the first line of each code chunk. <details>
    <summary>Details</summary>
    Available commands:

  * `r.selectCurrentChunk`
  * `r.runCurrentChunk`
  * `r.runAboveChunks`
  * `r.runCurrentAndBelowChunks`
  * `r.runBelowChunks`
  * `r.runAllChunks`
  * `r.runPreviousChunk`
  * `r.runNextChunk`
  * `r.goToPreviousChunk`
  * `r.goToNextChunk`
    <br>

    Customize both the commands AND its orders (that is, CodeLens respect user-specified orders). Default commands:
  * `r.runCurrentChunk`
  * `r.runAboveChunks`
  * `<Add item...>`
  </details>
* `r.rmarkdown.chunkBackgroundColor:` RMarkdown chunk background color in RGBA or RGB value.
  <details>
  <summary>Details</summary>
    Defaults to rgba(128, 128, 128, 0.1). Leave it empty to disable it (use default editor background color). Reload VS Code after changing settings. Learn how to set colors: https://www.w3schools.com/css/css_colors_rgb.asp
    <br><br>

    Examples for syntax `rgba(<red>, <green>, <blue>, <alpha>)`:
  * `rgba(128, 128, 128, 0.1)`
  * `rgba(128, 128, 128, 0.3)`
  * `rgba(255, 165, 0, 0.1)`
  </details>

