The R language service implements the [Language Server Protocol](https://microsoft.github.io/language-server-protocol/specifications/specification-current/) and provides a set of language analysis features such as completion, signature, hover, definition, references, diagnostics, etc.

The language service is provided by the R language server (implemented by [languageserver](https://github.com/REditorSupport/languageserver)) which performs static code analysis with the latest user documents in `R` and `Rmd` languages. Therefore, it does not rely on an active R session and thus does not require the code to be executed.

To install the package from CRAN:

```r
install.packages("languageserver")
```

To experience the latest features, install the package from GitHub:

```r
remotes::install_github("REditorSupport/languageserver")
```

## Settings

The following settings could be set up to deviate from the default behavior:

- `r.lsp.enabled`: Enable the R language service (default).
- `r.rpath.windows`, `r.rpath.mac`, `r.rpath.linux`: Path to R binary for launching the R Language Server package (see below). Examples: `/usr/bin/R` (Linux/macOS), `C:\\Program Files\\R\\R-4.1.0\\bin\\x64\\R.exe` (Windows). If the settings are left blank (default), then the R path will be detected from the `PATH` environment variable and Windows registry. It should be *vanilla* R rather than radian console.
- `r.lsp.args`: The command line arguments to use when launching R Language Server. Example: `--vanilla` to disable loading startup scripts such as `.Rprofile` and `Rprofile.site`.
- `r.lsp.debug`: Enable debugging traces. Defaults to `false`. Set this to `true` if you are having trouble getting the Language Server working.
- `r.lsp.diagnostics`: Enable linting of R code, using the [lintr](https://github.com/jimhester/lintr) package. Defaults to `true`. To disable this, you must have at least version 0.2.7 of the R Language Server installed.

## Completion

![Completion](https://user-images.githubusercontent.com/4662568/71432969-6fb3b200-2717-11ea-89a6-244cc7e38abf.gif)

![Scope completion](https://user-images.githubusercontent.com/4662568/71432977-717d7580-2717-11ea-9c2e-f76c811e6f0d.gif)

## Signature

![Package function signature](https://user-images.githubusercontent.com/4662568/71432976-717d7580-2717-11ea-898f-4eecfebe97b3.png)

![User function signature](https://user-images.githubusercontent.com/4662568/71432978-72160c00-2717-11ea-95fe-8b2d1930c7a9.png)

## Hover

![Hover](https://user-images.githubusercontent.com/4662568/71432974-70e4df00-2717-11ea-9f89-bfe5a363dbd3.gif)

## Document highlight

![Document highlight](https://user-images.githubusercontent.com/4662568/71432973-70e4df00-2717-11ea-906c-050ac17d79a7.gif)

## Document and workspace symbol

### Document outline

### Document symbol

![Document/workspace symbols](https://user-images.githubusercontent.com/4662568/86803613-bc098280-c0a8-11ea-9ca5-4732172cd835.gif)

### Code sections

![Code section symbols](https://user-images.githubusercontent.com/4662568/72678086-90381780-3add-11ea-9e93-0d7a4d1c1882.png)

## Diagnostics

![Diagnostics](https://user-images.githubusercontent.com/4662568/71432971-704c4880-2717-11ea-9ceb-fc35a091d839.png)

## Formatting

![Formatting](https://user-images.githubusercontent.com/4662568/71432972-70e4df00-2717-11ea-86b4-2da317e1376b.gif)

![On-type-formatting](https://user-images.githubusercontent.com/4662568/74438354-f0379900-4ea4-11ea-9743-99e8a8950d40.gif)

## Code actions



## Go to definition

![Definition](https://user-images.githubusercontent.com/4662568/71432970-704c4880-2717-11ea-9fc0-7f7ced962874.gif)

## Find references

![Find references](https://user-images.githubusercontent.com/4662568/93667495-fb951780-fab8-11ea-96bf-8649b89a85d7.gif)

## Rename symbol

![Rename symbol](https://user-images.githubusercontent.com/4662568/93668953-ef15bc80-fac2-11ea-9ea6-21e2e98517a1.gif)

## Call hierarchy

![Call Hierarchy](https://user-images.githubusercontent.com/4662568/106375983-e49df480-63cb-11eb-80ef-b1967a897b15.gif)

## Code folding

![Code section and function folding ranges](https://user-images.githubusercontent.com/4662568/86252664-135dad80-bbe6-11ea-8f89-55a81f2cc898.gif)

## Document link

![Link](https://user-images.githubusercontent.com/4662568/73524149-7e446600-4447-11ea-84a8-9fe152df7562.png)

## Color picker

![Document color](https://user-images.githubusercontent.com/4662568/73992222-5f832980-4989-11ea-9593-a58e97df47b5.png)

## Document selection

![Selection range](https://user-images.githubusercontent.com/4662568/104819407-3d1bb080-5868-11eb-95fb-7bc4c5f72469.gif)