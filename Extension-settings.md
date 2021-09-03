This extension contributes the following settings:

## General Editor Settings

* `r.source.encoding`: An optional encoding to pass to R when executing the file
* `r.source.focus`: Keeping focus when running (editor or terminal)
* `r.sessionWatcher`: Enable R session watcher (experimental)
* `r.session.watchGlobalEnvironment`: watch the global environment to provide hover, autocompletions, and workspace viewer information
* `r.session.levelOfObjectDetail`: how much of the object to show on hover, autocompletion, and in the workspace viewer?
  <details>
    <summary>Details</summary>
  Available options:

  * `minimal`: display literal values and object types only
  * `detailed`: display list content, data frame column values, and example values

  </details>
* `r.session.emulateRStudioAPI`: Emulate the RStudio API for addin support and other {rstudioapi} calls
* `r.session.viewers.viewColumn`: which view column should R-related webviews be displayed?
* `r.workspaceViewer.showObjectSize`: show object size when hovering over a workspace viewer item
* `r.workspaceViewer.clearPrompt`: prompt the user for confirmation when clearing the workspace

## Executable and Terminal Settings

* `r.rterm.windows`: set to R.exe path for Windows
* `r.rterm.mac`: set to R term's path for Mac OS X
* `r.rterm.linux`: set to R term's path for Linux
* `r.rpath.lsp`: set to R.exe path for Language Server Protocol
* `r.rterm.option`: R command line options (i.e: --vanilla)
* `r.alwaysUseActiveTerminal`: Use active terminal for all commands, rather than creating a new R terminal
* `r.bracketedPaste`: For consoles supporting bracketed paste mode (such as Radian)
* `r.rtermSendDelay`: Delay in milliseconds before sending each line to rterm (only applies if r.bracketedPaste is false)

## Plot Settings
* WIP

## R Markdown Settings

* `r.rmarkdown.enableCodeLens`: Enable RMarkdown CodeLens, which are inline commands/buttons e.g. 'Run Chunk | Run Above' shown on the first line of each code chunk.
  <details>
    <summary>Details</summary>

  * Click the buttons to run commands.
  * Hover on the buttons to show tooltips.
  * CodeLens commands are customizable via settings UI (Rmarkdown: Code Lens commands) or settings.json `r.rmarkdown.codeLensCommands`
  </details>
* `r.rmarkdown.codeLensCommands`: Customize RMarkdown CodeLens, which are inline commands/buttons e.g. 'Run Chunk | Run Above' shown on the first line of each code chunk.
  <details>
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
* `r.rmarkdown.preview.autoRefresh`: Enable automatic refresh of R Markdown preview on file update.

## Live Share Settings
* WIP