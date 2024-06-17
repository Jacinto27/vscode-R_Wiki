R code linting (diagnostics) is provided by [lintr](https://github.com/r-lib/lintr) via language server and is enabled by default. It provides syntax error warnings as well as style guidelines.

To customize the linting behavior, create (or edit) a global lintr config file in your home directory `${user.name}/.lintr`.You can also have a project-specific lintr configuration by creating a config file at `${workspaceFolder}/.lintr`.

You can configure the behavior of your linter by editing the contents of the file, here are some examples:

- Only detect syntax errors:

```
linters: list()
```

- Deviate from [default linters](https://lintr.r-lib.org/reference/default_linters.html):

Adjust the number of characters in each line for `line_length_linter` and disable `commented_code_linter`.

```
linters: linters_with_defaults(
    line_length_linter(120),
    commented_code_linter = NULL
  )
```

- Only use specified linters:

```
linters: list(
  commas_linter(),
  duplicate_argument_linter(),
  missing_argument_linter(),
  missing_package_linter(),
  namespace_linter())
```

- Here are some suggested configurations: _THIS EDIT IS OPTIONAL; REMOVE IN REVIEW IF NOT CONSIDERED APPROPRIATE_

```
linters: linters_with_defaults(
   line_length_linter    = NULL, # Line lenght warning, default was 120 characters
   cyclocomp_linter      = NULL, # Checks for overly complex equations, turned off
   object_name_linter    = NULL, # Enforces the use of snake_case names in objects, turned off
   object_usage_linter   = NULL, # Warns about declared variables that are never used, turned off
   commented_code_linter = NULL, # Does not warn about commented lines of code
   assignment_linter     = NULL, # Does not enforce the use of '<-' for value assignement
   seq_linter           = NULL,  # Does not enforce the usage of seq_len() in for loops
   semicolon_linter      = NULL) # Does not enforce the usage of semicolons at the end of expressions.
```

Visit [Individual linters](https://lintr.r-lib.org/reference/index.html#individual-linters) for a complete list of supported linters.

To disable diagnostics, you might add the following to the VS Code settings:

```json
{
  "r.lsp.diagnostics": false
}
```

However, you will not be notified if syntax errors in the code are detected.

Visit the [Configuring linters](https://lintr.r-lib.org/articles/lintr.html#configuring-linters) for a complete guide to customizing lintr config regarding the list of linters and file or line exclusions.
