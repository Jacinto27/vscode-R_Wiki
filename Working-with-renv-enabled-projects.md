[renv](https://rstudio.github.io/renv/articles/renv.html) is a package that helps manage library paths to help isolate your project’s R dependencies for better reproducibility of the project.

Since `renv` uses a private library per project, vscode-R will not work if required packages (e.g. `languageserver` and `jsonlite`) are not installed into the project library. Some users might find it useful to maintain a standalone, minimal user library to provide these packages.

Suppose we want to maintain such a library at `~/R/vscode-R` using renv.

```r
renv::init(project = "~/R/vscode-R")
```

Start R from the folder (`path.expand("~/R/vscode-R")`) and install required packages:

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

Then the following R processes running in the background will be launched with the configured library paths appended to `.libPaths()` on startup:

* R language server
* R help server
* R aliases

And the code editing features and help viewer could continue to work without necessary packages being installed into the project library.

---

When working with `Rcpp`, a good demo is provided at [vscode-rcpp-demo](https://github.com/renkun-ken/vscode-rcpp-demo). If you're working with `renv`, the `includePath` property in `.vscode/c_cpp_properties.json` needs to manually be pointed at your project's `R_LIBS_USER` directory. Exempli gratia: 

```
/Users/user/Library/Caches/org.R-project.R/R/renv/library/vscode-rcpp-demo-e5908179/macos/R-4.4/aarch64-apple-darwin20
# becomes
/Users/user/Library/Caches/org.R-project.R/R/renv/library/vscode-rcpp-demo-e5908179/macos/R-4.4/aarch64-apple-darwin20/*/include/
```
