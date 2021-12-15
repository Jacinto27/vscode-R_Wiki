For many R users, [RStudio](https://github.com/rstudio/rstudio) has long been a
great integrated development environment for data analysis and visualization. It
provides a rich set of features that make it unprecedentedly easy to perform a
wide range of tasks interactively.

[VS Code](https://code.visualstudio.com/), in contrast, is not specifically
designed for a certain programming language. It is highly customizable through
[settings](https://code.visualstudio.com/docs/getstarted/settings), and highly
extensible through [extensions](https://marketplace.visualstudio.com/). It
supports many programming languages at different levels through language
extensions that implement some common protocols such as the
[Language Server Protocol](https://microsoft.github.io/language-server-protocol)
to enable language features based on code analysis such as _Go To Definition_
and _Rename symbol_, and the
[Debug Adapter Protocol](https://microsoft.github.io/debug-adapter-protocol/) to
enable interactive debugging of any target.

This vscode-R extension is an extension that attempts to make it easier to write
R code and work with R sessions interactively in VS Code. Though vscode-R
[provides support](https://github.com/REditorSupport/vscode-R/wiki/RStudio-addin-support)
emulating RStudio's features, it is not intended to be a full drop-in
replacement for RStudio. In contrast, vscode-R is useful for those who want a
unified development environment to work with multiple programming languages such
as R, Python, C++, etc., as well as those who need to work with remote servers,
containers, self-managed R sessions or multiple R sessions at the same time.

To enjoy the full R development experience, we recommend that you install all of
the following packages:

- [vscode-R](https://marketplace.visualstudio.com/items?itemName=Ikuyadeu.r):
  Provides R language service, R Markdown, and interactivity between VS Code and
  R terminal.

- [languageserver](https://github.com/REditorSupport/languageserver): An R
  package that implements the Language Server Protocol for R to provide a wide
  range of language analysis features such as auto-completion, function
  signature, documentation, symbol highlight, document outline, code formatting,
  symbol hover, diagnostics, go to definition, find references, etc.

- [radian](https://github.com/randy3k/radian): A modern R console that corrects
  many limitations of the official R terminal and supports many features such as
  syntax highlighting and auto-completion.

- [VSCode-R-Debugger](https://github.com/ManuelHentschel/VSCode-R-Debugger): A
  VS Code extension to support R debugging capabilities.

- [`httpgd`](https://github.com/nx10/httpgd): An R package to provide a graphics
  device that asynchronously serves SVG graphics via HTTP and WebSockets.
  vscode-R uses `httpgd` to provide an interactive
  [plot viewer](https://github.com/REditorSupport/vscode-R/wiki/Plot-viewer).

- [rmarkdown](https://rmarkdown.rstudio.com): An R package and format for
  creating reproducible and narrative-driven data analyses. vscode-R provides
  tooling to edit, run, and knit Rmarkdown files.

- [Pandoc](https://pandoc.org) (optional): A powerful document conversion tool.
  vscode-R uses this to render help previews when users hover over R code.

However, the astounding flexibility of VS Code comes at a cost that some users
might not find enjoyable in the beginning: Some setup and configuration are
needed to make each part work well together. To minimize that cost, please refer
to the installation guidelines on the right side and see the installation
instructions we provide in details on Windows, Linux and macOS.
