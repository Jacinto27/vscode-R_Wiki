## Creating R terminal

In VS Code window, press <kbd>F1</kbd> (or <kbd>Ctrl + Shift + P</kbd>) and choose "R: Create R terminal" command, then the VS Code terminal will be revealed and an R terminal will be launched.

By default, the official `R` terminal is launched.

<img width="617" alt="R" src="https://user-images.githubusercontent.com/4662568/122424170-156c7800-cfc1-11eb-8e5d-748e63022440.png">

We recommend [radian](https://github.com/randy3k/radian) as a better alternative.

<img width="617" alt="radian" src="https://user-images.githubusercontent.com/4662568/122424434-4d73bb00-cfc1-11eb-9141-c0fb6561a068.png">

If the R session watcher is enabled, then it will attach to the R session whenever a new R terminal is created. The status of the session watcher is shown in the status bar like below:

![status](https://github.com/Ikuyadeu/vscode-R/blob/master/images/RStatusBarItem.png)

## Sending code to R terminals

By default, if there is no active R terminal, then a new R terminal will be created before sending code to it. To always send code to the active terminal without creating a new one, turn on `r.alwaysUseActiveTerminal` in VS Code settings.

The behavior of sending code to the terminal is following:

* If a range of code is selected, then the selected code will be sent to the terminal.
* If no code is selected, then an executable range of code will be sent to the terminal and the cursor will move to the next line.

## Using multiple R terminals

Each time "R: Create R terminal" is executed, a new R terminal is created. The user could switch between these R terminals, and customize the icon color and the label of each terminal.

<img width="618" alt="R terminals" src="https://user-images.githubusercontent.com/4662568/122424572-67ad9900-cfc1-11eb-9448-9bf9413b06c3.png">

To make the session watcher attach the R session of the current R terminal, click the status bar item "R: (not attached)" or "R: #PID" if a session is previously attached.

## Using self-managed R terminals

Self-managed R terminals could be useful if one needs one or more R sessions to be preserved so that closing the VS Code window does not  terminate the R sessions. On Linux and macOS, both [`screen`](https://www.gnu.org/software/screen/) and [`tmux`](https://github.com/tmux/tmux/wiki) could be used to preserve any number of R sessions or any other terminal programs in a customizable layout.

<img width="651" alt="radian in tmux" src="https://user-images.githubusercontent.com/4662568/122424856-9f1c4580-cfc1-11eb-8825-a4ad2b2c9251.png">

To make self-managed R sessions behave like those created by "R: Create R terminal", the following code should be added to `~/.Rprofile`:

```r
if (interactive() && Sys.getenv("RSTUDIO") == "") {
  Sys.setenv(TERM_PROGRAM = "vscode")
  source(file.path(Sys.getenv(if (.Platform$OS.type == "windows") "USERPROFILE" else "HOME"), ".vscode-R", "init.R"))
}
```

Then starting an R terminal anywhere will request the session watcher to attach the R session.