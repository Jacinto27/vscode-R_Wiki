*This experimental feature is still under development and the behavior
**may change without notice**. Please file an issue [here](https://github.com/Ikuyadeu/vscode-R/issues) if you experience problems or have any suggestions.*

An opt-in experimental R session watcher is implemented to support the following features:

* Watch any R session
* Show value of session symbols on hover
* Provide completion for session symbols
* `View()` any objects including data frames and list objects
* Show plot output on update and plot history
* Show htmlwidgets, documentation and shiny apps in WebView

### Basic usage

To enable this feature, turn on `r.sessionWatcher` in VSCode settings, reload or restart VSCode, and the session watcher will be activated automatically
on R sessions launched by vscode-R via `R: Create R Terminal` command.

*If you previously appended the `source(...)` line to `~/.Rprofile`, you may safely remove it since the configuration for basic usage is automated. It is
now only necessary for advanced usage described below.*

### Advanced usage (for self-managed R sessions)

For advanced users to work with self-managed R sessions (e.g. manually launched R terminal or started in `tmux` or `screen` window), some extra
configuration is needed. Follow the steps below to make R session watcher work with any external R session:

1. Turn on `r.sessionWatcher` in VSCode settings.
2. Edit `.Rprofile` in your home directory by running the following code in R:

    ```r
    file.edit("~/.Rprofile")
    ```

3. Append the following code to the file:

    ```r
    source(file.path(Sys.getenv(if (.Platform$OS.type == "windows") "USERPROFILE" else "HOME"), ".vscode-R", "init.R"))
    ```

4. Restart or Reload Window in VSCode

If the workspace folder you open in VSCode already has a `.Rprofile`, you need to append the code above in this file too because `~/.Rprofile` will not
be executed when a local `.Rprofile` is found.

The script only works with environment variable `TERM_PROGRAM=vscode`. the script will not take effect with R sessions started in a `tmux` or `screen` window that does not have it, unless this environment variable is manually set before sourcing `init.R`, for example, you may insert a line `Sys.setenv(TERM_PROGRAM="vscode")` before it.

### Available functions and options

When the session watcher is initialized on session startup, a local environment named `tools:vscode` is attached and the following functions are made available for user to interoperate with VSCode:

```r
# Attach vscode-R with same workspace folder to current session.
.vsc.attach()

# A customizable View() where title and viewer can be specified.
.vsc.view(x, title, viewer)

# Browse an URL in a WebView (used by e.g. shiny apps, R html help).
.vsc.browser(url, title, ..., viewer)

# Show viewer from a HTML file or htmlwidget object (used by most htmlwidgets).
.vsc.viewer(url, title, ..., viewer)

# Show page viewer from a HTML file or htmlwidget object (used by e.g. profvis).
.vsc.page_viewer(url, title, ..., viewer)
```

All WebView-related functions have a `viewer` argument which could be one of the values defined in [vscode-api#ViewColumn](https://code.visualstudio.com/api/references/vscode-api#ViewColumn), .e.g. `"Active"` (current editor), `"Two"` (editor group 2), or `"Besides"` (always show besides the current editor).

The following options are available for user to customize the session watcher functionality and behavior:

```r
# Watch global environemnt symbols to provide hover on and completion after session symbol.
# Only specify in .Rprofile since it only takes effect on session startup.
options(vsc.globalenv = TRUE | FALSE)

# Which view column to show the plot file on graphics update
# Use FALSE to diable plot watcher so that the default R plot device is used.
# Only specify in .Rprofile since it only takes effect on session startup.
options(vsc.plot = "Two" | "Active" | "Besides" | FALSE)

# The arguments for the png device to replay user graphics to show in VSCode.
# Ignored if options(vsc.plot = FALSE).
options(vsc.dev.args = NULL | list(width = 800, height = 600))

# Which view column to show the WebView triggered by browser (e.g. shiny apps)?
# Use FALSE to open in external web browser.
options(vsc.browser = "Active" | "Besides" | "Two" | FALSE)

# Which view column to show the WebView triggered by viewer (e.g. htmlwidgets)?
# Use FALSE to open in external web browser.
options(vsc.viewer = "Two" | "Active" | "Besides" | FALSE)

# Which view column to show the WebView triggered by page_viewer (e.g. profvis)?
# Use FALSE to open in external web browser.
options(vsc.page_viewer = "Active" | "Besides" | "Two" | FALSE)

# Which view column to show the WebView triggered by View()?
# Use FALSE for R's native View(), which should be specified in .Rprofile
#   since it only takes effect on session startup.
options(vsc.view = "Two" | "Active" | "Besides" | FALSE)
```

The first values are the default and all subsequent values after `|` are available choices.
The `"Two" | "Active" | "Besides"` are popular values from `ViewColumn` to specify which view column should the corresponding tab appears in VSCode.

### How to disable it

For the case of basic usage, turning off `r.sessionWatcher` in VSCode settings is sufficient
to disable R session watcher.

For the case of advanced usage, user should, in addition, comment out or remove the `source(...)` line appended to `~/.Rprofile`.

### How it works

* When vscode-R is activated with session watcher enabled, it deploys the initialization script to `~/.vscode-R/init.R`.
* vscode-R watches `~/.vscode-R/request.log` for requests from user R sessions.
* When a new R session is created, it sources `init.R` to initialize the session watcher and writes attach request to `~/.vscode-R/request.log`.
* vscode-R reads the attach request and knows the working directory and session temp directory (`{tempDir}`) of the attaching session.
* vscode-R watches `{tempDir}/vscode-R/globalenv.json` for global environment info and `{tempDir}/vscode-R/plot.png` for plot graphics.
* In the R session, the global environment info will be updated on each evaluation of top-level expression.
* When user creates or updates a plot, the `{tempDir}/vscode-R/plot.png` is updated, and vscode-R will open the plot file.
* When user calls `View()` with a data frame, list, environment, or any other object, the request is written to `~/.vscode-R/request.log` and
vscode-R will open a WebView to show the data or open a text document to show the content of the object.
* When user calls the viewer (e.g. htmlwidget, provis) or browser (e.g. shiny app, HTML help documentation), the request is written to `~/.vscode-R/request.log` and vscode-R will open a WebView to present the viewer content.

R sessions started from the workspace root folder or a subfolder will be automatically attached. The session watcher is designed to work in a wide range of scenarios:

* Official R terminal or `radian` console
* R session started by vscode-R or user
* R session in a `tmux` or `screen` window
* Multiple R sessions in VSCode terminal
* Multiple R sessions in `tmux` windows or panes.
* Multi-root workspace in VSCode
* Switch between multiple running R sessions
* [Remote Development](https://code.visualstudio.com/docs/remote/remote-overview) via SSH, WSL and Docker

The status bar item shows the process id of the attached R session. Click the status bar item and it will
attach to currently active session.

![Attached R process](./images/RStatusBarItem.png)

![R session watcher](https://user-images.githubusercontent.com/4662568/70815935-65391480-1e09-11ea-9ad6-7ebbebf9a9c8.gif)

*The R terminal used in the screenshot is [radian](https://github.com/randy3k/radian) which is cross-platform and
supports syntax highlighting, auto-completion and many other features.*
