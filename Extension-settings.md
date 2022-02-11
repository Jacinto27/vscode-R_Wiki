This page details the settings of vscode-R that can be set in VSCode's
`settings.json` file.

Please also see
[recommend extensions and configurations](https://github.com/REditorSupport/vscode-R/wiki/R-Language-Service),
some
[useful keyboard shortcuts](https://github.com/REditorSupport/vscode-R/wiki/Keyboard-shortcuts)
and the options for the language server's formatter and linter that are detailed
[here](https://github.com/REditorSupport/languageserver#faq).

## General Editor Settings

- `r.source.encoding`: an optional encoding to pass to R when executing the file
- `r.source.focus`: keeping focus when running (editor or terminal)
- `r.sessionWatcher`: enable R session watcher
- `r.session.watchGlobalEnvironment`: watch the global environment to provide
  hover, autocompletions, and workspace viewer information
- `r.session.levelOfObjectDetail`: how much of the object to show on hover,
  autocompletion, and in the workspace viewer?
  <details>
    <summary>Details</summary>
  Available options:

  - `minimal`: display literal values and object types only
  - `detailed`: display list content, data frame column values, and example
    values

  </details>

- `r.session.emulateRStudioAPI`: emulate the RStudio API for addin support and
  other {rstudioapi} calls
- `r.session.viewers.viewColumn`: which view column should R-related webviews be
  displayed?
- `r.workspaceViewer.showObjectSize`: show object size when hovering over a
  workspace viewer item
- `r.workspaceViewer.clearPrompt`: prompt the user for confirmation when
  clearing the workspace

## Executable and Terminal Settings

- `r.rterm.windows`: set to R.exe path for Windows
- `r.rterm.mac`: set to R term's path for Mac OS X
- `r.rterm.linux`: set to R term's path for Linux
- `r.rpath.lsp`: set to R.exe path for Language Server Protocol
- `r.rterm.option`: R command line options (i.e: --vanilla)
- `r.alwaysUseActiveTerminal`: use active terminal for all commands, rather than
  creating a new R terminal
- `r.bracketedPaste`: for consoles supporting bracketed paste mode (such as
  Radian)
- `r.rtermSendDelay`: delay in milliseconds before sending each line to rterm
  (only applies if r.bracketedPaste is false)

## Plot Settings

- `r.plot.useHttpgd`: use the httpgd-based plot viewer instead of the base
  VSCode-R plot viewer
- `r.plot.defaults.colorTheme`: which color theme to use when launching the plot
  viewer
- `r.plot.defaults.plotPreviewLayout`: how to display plot previews if more than
  one row required
- `r.plot.defaults.fullWindowMode`: whether to use full window mode when
  launching the plot viewer
- `r.plot.timing.resizeInterval`: interval in ms to wait between plot resizes
- `r.plot.timing.refreshInterval`: interval in ms to wait between plot refreshs
- `r.plot.customStyleOverwrites`: path to a custom CSS file to be used when
  r.plot.defaults.colorTheme is 'vscode'. Replaces the default CSS overwrites!

## Data viewer Settings

- `r.session.data.rowLimit`: The maximum number of rows to be displayed in the data viewer.
  `0` means no limit.

## R Markdown Settings

- `r.rmarkdown.enableCodeLens`: enable RMarkdown CodeLens, which are inline
  commands/buttons e.g. 'Run Chunk | Run Above' shown on the first line of each
  code chunk.
  <details>
    <summary>Details</summary>

  - Click the buttons to run commands.
  - Hover on the buttons to show tooltips.
  - CodeLens commands are customizable via settings UI (Rmarkdown: Code Lens
  commands) or settings.json `r.rmarkdown.codeLensCommands`
  </details>

- `r.rmarkdown.codeLensCommands`: Customize RMarkdown CodeLens, which are inline
  commands/buttons e.g. 'Run Chunk | Run Above' shown on the first line of each
  code chunk.
  <details>
    <summary>Details</summary>
    Available commands:

  - `r.selectCurrentChunk`
  - `r.runCurrentChunk`
  - `r.runAboveChunks`
  - `r.runCurrentAndBelowChunks`
  - `r.runBelowChunks`
  - `r.runAllChunks`
  - `r.runPreviousChunk`
  - `r.runNextChunk`
  - `r.goToPreviousChunk`
  - `r.goToNextChunk` <br>

    Customize both the commands AND its orders (that is, CodeLens respect
    user-specified orders). Default commands:

  - `r.runCurrentChunk`
  - `r.runAboveChunks`
  - `<Add item...>`
  </details>

- `r.rmarkdown.chunkBackgroundColor:` RMarkdown chunk background color in RGBA
  or RGB value.

  <details>
    <summary>Details</summary>

  Defaults to rgba(128, 128, 128, 0.1). Leave it empty to disable it (use
  default editor background color). Reload VS Code after changing settings.
  Learn how to set colors: <https://www.w3schools.com/css/css_colors_rgb.asp>

  <br><br>

  Examples for syntax `rgba(<red>, <green>, <blue>, <alpha>)`:

  - `rgba(128, 128, 128, 0.1)`
  - `rgba(128, 128, 128, 0.3)`
  - `rgba(255, 165, 0, 0.1)`
  </details>

- `r.rmarkdown.preview.autoRefresh`: Enable automatic refresh of R Markdown
  preview on file update.

## Live Share Settings

- `r.liveShare.timeout`: time in milliseconds before aborting attempt to connect
  to Live Share API
- `r.liveShare.defaults.commandForward`: default boolean value for guest command
  forwarding.
- `r.liveShare.defaults.shareWorkspace`: default boolean value for sharing the R
  workspace with guests
- `r.liveShare.defaults.shareBrowser`: default boolean value for automatically
  sharing R browser ports with guests

## Language server settings

The following settings could be set up to deviate from the default behavior:

- `r.lsp.enabled`: Enable the R language server (default).
- `r.rpath.windows`, `r.rpath.mac`, `r.rpath.linux`: Path to R binary for
  launching the R Language Server package (see below). Examples: `/usr/bin/R`
  (Linux/macOS), `C:\\Program Files\\R\\R-4.1.0\\bin\\x64\\R.exe` (Windows). If
  the settings are left blank (default), then the R path will be detected from
  the `PATH` environment variable and Windows registry. It should be _vanilla_ R
  rather than radian console.
- `r.lsp.args`: The command line arguments to use when launching R Language
  Server. Example: `--vanilla` to disable loading startup scripts such as
  `.Rprofile` and `Rprofile.site`.
- `r.lsp.debug`: Enable debugging traces. Defaults to `false`. Set this to
  `true` if you are having trouble getting the Language Server working.
- `r.lsp.diagnostics`: Enable linting of R code, using the
  [lintr](https://github.com/jimhester/lintr) package. Defaults to `true`. To
  disable this, you must have at least version 0.2.7 of the R Language Server
  installed.
