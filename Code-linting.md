R code linting (diagnostics) is provided by [lintr](https://github.com/r-lib/lintr) via language server and is enabled by default.

To disable diagnostics, you might add the following to the VS Code settings:

```json
{
  "r.lsp.diagnostics": false
}
```

However, you will not be notified if syntax errors in the code are detected.

To customize the linting behavior, edit the global lintr config file at `~/.lintr`, or project-specific lintr config file at `${workspaceFolder}/.lintr`.

The following are some examples:

* Only detect syntax errors:

```
linters: list()
```

* Deviate from [default linters](https://lintr.r-lib.org/reference/default_linters.html):

Adjust the number of characters in each line for `line_length_linter` and disable `commented_code_linter`.

```
linters: linters_with_defaults(
    line_length_linter(120), 
    commented_code_linter = NULL
  )
```

* Only use specified linters:

```
linters: list(
  commas_linter(),
  duplicate_argument_linter(),
  missing_argument_linter(),
  missing_package_linter(),
  namespace_linter())
```

Visit [Individual linters](https://lintr.r-lib.org/reference/index.html#individual-linters) for a complete list of supported linters.

Visit the [Configuring linters](https://lintr.r-lib.org/articles/lintr.html#configuring-linters) for a complete guide to customizing lintr config regarding the list of linters and file or line exclusions.