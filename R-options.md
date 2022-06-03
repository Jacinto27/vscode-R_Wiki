This page details the settings of vscode-R that can be set inside R via the `options()` command. Please note that the majority of R options listed can also be set by various [vscode-R extension settings](https://github.com/REditorSupport/vscode-R/wiki/Extension-settings). If an option is set in both R and vscode-R, the R option will be preferenced.

## General settings
- `vsc.rstudioapi`: emulate the RStudio API for addin support and other {rstudioapi} calls

## VSCode Viewer positions

- `vsc.plot`
- `vsc.browser`
- `vsc.viewer`
- `vsc.page_viewer`
- `vsc.view`
- `vsc.helpPanel`

<details>
  <summary>Details</summary>
   Available options:

  - `"Two"`
  - `"Active"`
  - `"Beside"`
  - `FALSE`

</details>

## Environment
- `vsc.globalenv`: watch the global environment to provide hover, autocompletions, and workspace viewer information
- `vsc.str.max.level`: how much of the object to show on hover and autocomplete detail?
- `vsc.object_length_limit`: upper limit of object length to show object details in workspace viewer and provide session symbol completion
- `vsc.object_timeout`: maximum number of milliseconds to get information of a single object in the global environment
- `vsc.show_object_size`: show object size in the workspace viewer tooltip
- `vsc.row_limit`: the maximum number of rows to be displayed in the data viewer

## Plotting
- `vsc.use_httpgd`: use the httpgd-based plot viewer instead of the base VSCode-R plot viewer
- `vsc.dev.args`: the arguments for the png device to replay user graphics in VSCode
  <details>
    <summary>Details</summary>
  Available options:

  - `NULL`
  - `list(width = , height = )`

  </details>

