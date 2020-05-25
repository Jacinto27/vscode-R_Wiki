*This experimental feature is still under development and the behavior
**may change without notice**. Please file an issue [here](https://github.com/Ikuyadeu/vscode-R/issues) if you experience problems or have any suggestions.*

An opt-in experimental R session watcher is implemented to support the following features:

* Watch any R session
* Show value of session symbols on hover
* Provide completion for session symbols
* `View()` any objects including data frames and list objects
* Show plot output on update and plot history
* Show htmlwidgets, documentation and shiny apps in WebView

Known limitations:

* Session watcher only works when the R session is started from the workspace folder in VSCode.
* Session watcher may not work with folders under some cloud drives (e.g. Google Drive, OneDrive) but works with iCloud Drive on macOS.

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

### How to disable it

For the case of basic usage, turning off `r.sessionWatcher` in VSCode settings is sufficient
to disable R session watcher.

For the case of advanced usage, user should, in addition, comment out or remove the `source(...)` line appended to `~/.Rprofile`.

### How it works

This script writes the metadata of symbols in the global environment and plot file to `${workspaceFolder}/.vscode/vscode-R/PID` where `PID` is the R process ID. It also captures user input and append command lines to `${workspaceFolder}/.vscode/vscode-R/response.log`, which enables the communication between vscode-R and a live R sesson.

Each time the extension is activated, the latest session watcher script (`init.R`) will be deployed to `~/.vscode-R/init.R`.

R sessions started from the workspace root folder will be automatically attached. The session watcher is designed to work in a wide range of scenarios:

* Official R terminal or `radian` console
* R session started by vscode-R or user
* R session in a `tmux` or `screen` window
* Switch between multiple running R sessions
* [Remote Development](https://code.visualstudio.com/docs/remote/remote-overview) via SSH, WSL and Docker

The status bar item shows the process id of the attached R session. Click the status bar item and it will
attach to currently active session.

![Attached R process](./images/RStatusBarItem.png)

![R session watcher](https://user-images.githubusercontent.com/4662568/70815935-65391480-1e09-11ea-9ad6-7ebbebf9a9c8.gif)

*The R terminal used in the screenshot is [radian](https://github.com/randy3k/radian) which is cross-platform and
supports syntax highlighting, auto-completion and many other features.*
