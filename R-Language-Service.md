The R language service implements the [Language Server Protocol](https://microsoft.github.io/language-server-protocol/specifications/specification-current/) and provides a set of language analysis features such as completion, signature, hover, definition, references, diagnostics, etc.

The language service is provided by the R language server (implemented by [languageserver](https://github.com/REditorSupport/languageserver)) which does static code analysis with the latest user documents in `R` and `Rmd` languages. The package is required to enable the language service:

```r
install.packages("languageserver")
```

## Settings

The following settings could be set up to deviate from the default behavior:

- `r.lsp.enabled`: Enable the R language service (default).
- `r.rpath.windows`, `r.rpath.mac`, `r.rpath.linux`: Path to R binary for launching the R Language Server package (see below). Examples: `/usr/bin/R` (Linux/macOS), `C:\\Program Files\\R\\R-4.1.0\\bin\\x64\\R.exe` (Windows). If the settings are left blank (default), then the R path will be detected from Windows registry and `PATH` environment variable. It should be *vanilla* R rather than radian console.
- `r.lsp.args`: The command line arguments to use when launching R Language Server. Example: `--vanilla` to disable loading startup scripts such as `.Rprofile` and `Rprofile.site`.
- `r.lsp.debug`: Enable debugging traces. Defaults to `false`. Set this to `true` if you are having trouble getting the Language Server working.
- `r.lsp.diagnostics`: Enable linting of R code, using the [lintr](https://github.com/jimhester/lintr) package. Defaults to `true`. To disable this, you must have at least version 0.2.7 of the R Language Server installed.

## Completion

## Signature

## Hover

## Document highlight

## Document symbol

## Workspace symbol

## Diagnostics

## Formatting

## Code actions

## Go to definition

## Find references

## Rename symbol

## Call hierarchy

## Code folding

## Document link

## Color picker

## Document selection
