Plot could be displayed in a VS Code editor tab.

## PNG file

When R session watcher is enabled, the default behavior of displaying graphics is to replay the plots to a `png` device created over a temporary PNG file. Whenever the plot is updated, the PNG file is revealed in VS Code in an image viewer.

<img width="919" alt="png file" src="https://user-images.githubusercontent.com/4662568/122624089-42a84b80-d0d1-11eb-8540-3fb837fdcd15.png">

There are known limitations of PNG plot viewer:

* If the plot contains multiple pages (e.g. `par(mfrow =)` is used), then the last page will overwrite the previous pages.
* If the code has multiple plot calls, each creating a new plot, then only the last plot will be captured.
* Some plot code based on `grid` package may not work as the plot updates cannot be captured.

## Native plot window

If the PNG plot viewer is not working properly, one might want to disable it with the following code in `~/.Rprofile`:

```r
options(vsc.plot = FALSE)
```

Then the plot viewer will fall back to the native plot window. It only takes effect on R session startup.

<img width="926" alt="native plot window" src="https://user-images.githubusercontent.com/4662568/122624019-feb54680-d0d0-11eb-944a-3c00b7fdf556.png">

## SVG in httpgd plot viewer

vscode-R supports an SVG plot viewer based on httpgd. Enable `r.plot.useHttpgd` in VS Code settings.

Then whenever a plot is created, a Plot viewer tab will be revealed where a number of httpgd features are natively supported.

<img width="916" alt="plot viewer" src="https://user-images.githubusercontent.com/4662568/122624181-974bc680-d0d1-11eb-99a9-59a34e105ad8.png">

## SVG in httpgd webpage

[httpgd](https://github.com/nx10/httpgd) is an R package to provide a graphics device that asynchronously serves SVG graphics via HTTP and WebSockets. It works well with VS Code in a browser viewer.

Before using httpgd, install the package via

```r
install.packages("httpgd")
```

To use httpgd as the default graphics device and make it automatically show up in VS Code, put the following code in `~/.Rprofile`:

```r
if (interactive() && Sys.getenv("RSTUDIO") == "") {
  Sys.setenv(TERM_PROGRAM = "vscode")
  if ("httpgd" %in% .packages(all.available = TRUE)) {
    options(vsc.plot = FALSE)
    options(device = function(...) {
      httpgd::hgd(silent = TRUE)
      .vsc.browser(httpgd::hgd_url(history = FALSE), viewer = "Beside")
    })
  }
  source(file.path(Sys.getenv(if (.Platform$OS.type == "windows") "USERPROFILE" else "HOME"), ".vscode-R", "init.R"))
}
```

<img width="915" alt="httpgd webpage" src="https://user-images.githubusercontent.com/4662568/122624135-73888080-d0d1-11eb-93e8-f94935d944cb.png">

The httpgd web page supports live update on resizing, history navigation, zooming, save as png format, and some other great features.

