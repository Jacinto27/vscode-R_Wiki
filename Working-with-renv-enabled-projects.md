[renv](https://rstudio.github.io/renv/articles/renv.html) is a package that helps manage library paths to help isolate your project’s R dependencies for better reproducibility of the project.

Since renv uses a private library per project, vscode-R will not work if required packages (e.g. `languageserver` and `jsonlite`) are not installed into the project library. Some users might find it useful to maintain a standalone, minimal user library to provide these packages.

Suppose we want to maintain such a library at `~/R/vscode-R` using renv.

```r
renv::init(project = "~/R/vscode-R")
```

Start R from the folder (`file.expand("~/R/vscode-R")`) and install required packages:

```r
renv::install(c("languageserver"))
```

Print the library path:

```r
renv::paths$library()
```

```
[1] "/Users/user/R/vscode-R/renv/library/R-4.2/x86_64-apple-darwin17.0"
```

Write the library path in VS Code settings:

```json
"r.libPaths": [
  "/Users/user/R/vscode-R/renv/library/R-4.2/x86_64-apple-darwin17.0"
]
```