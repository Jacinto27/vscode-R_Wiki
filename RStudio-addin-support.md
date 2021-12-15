The VSCode-R extension is compatible with a subset of RStudio Addins via an
`{rstudioapi}` emulation layer. Nearly all of the document inspection and
manipulation API is supported, although with some notable concessions:

- VSCode always directs addin text output destined for the "active document" to
  the active or last active text editor, and never the active terminal/console.

There are two main ways to launch an addin:

1. via the addin picker, launched from the command palette as "R: Launch RStudio
   Addin", or via a keybinding to `r.lauchAddinPicker`.
2. via a direct keybinding to the addin R functions. These can be found by
   looking in the `inst/rstudion/addins.dcf` file of the
   addin-providing-package's source. For example to bind a key to Reprex the
   current selection, you would configure a keybinding like:

```json
{
  "description": "reprex selection",
  "key": "ctrl+;",
  "command": "r.runCommand",
  "when": "editorTextFocus",
  "args": "reprex::reprex_selection"
}
```

## Enabling RStudio Addin Support

To enable RStudio addin support set the following options in your `~/.Rprofile`:

```r
options(vsc.rstudioapi = TRUE)
```

Place the option above any call to `source()` that refers to `init.R` in the
`.Rprofile`. Unless using self-managed R sessions, `init.R` should be called
automatically by the extension.

## Installing addins

Unlike RStudio the VSCode addin registry is regenrated every time a new R
session is attached, not when a new package is installed. You can use the
`.vsc.attach()` to re-attach an active R session, or
`rstudioapi::restartSession()` to restart the R session and repopulate installed
addins.

## Shiny Gadgets

Addins that launch Shiny gadgets and call supported functions can work, although
for best results, consider setting: `options(vsc.viewer = "Beside")` to have the
gadget open up alongside the active text editor.

## Known compatible packages

Packages listed here have been verified working in VSCode.

- `{datapasta}` dev version
- `{reprex}`
- `{fnmate}`
- `{equisse}`
- `{remedy}`
- `{AlignAssign}`
- `{blogdown}`
  - Live preview in VSCode works but viewer colour theme interacts with site
    colour theme. Choose a light theme for light site preview.
- `{docthis}`
- `{sinew}`
  - The interactive oxygen generator polls the active document_context, which is
    glitchy but can work.
- `{prefixer}`
- `{gistfo}`
- `{citr}`
- `{styler}`

## Implemented functions

`{rstudioapi}` Functions in this section have been reimplemented to work with
VSCode:

- `getActiveDocumentContext`
- `getSourceEditorContext`
- `isAvailable`
- `verifyAvailable`
- `insertText`
- `modifyRange`
- `readPreference`
- `readRStudioPreference`
- `hasFun`
- `findFun`
- `showDialog`
- `navigateToFile`
- `setSelectionRanges`
- `setCursorPosition`
- `setDocumentContents`
- `documentSave`
- `documentId`
- `documentPath`
- `documentSaveAll`
- `documentNew`
- `getActiveProject`
- `restartSession`
- `viewer`

## Unimplemented functions

Functions not above that need to interact with the IDE to work have been
reassigned to stop with an error:

`This {rstudioapi} function is not currently implemented for VSCode.`

# Developer notes

The best way to check if an IDE API function is supported in a way that is
supported by both RStudio and VSCode is to call `hasFun` or `findFun`. This will
work as expected for all implemented functions above.

`rstudioapi` offers the ability to assert certain version numbers of the IDE
whilst using these functions with a `version_needed` argument. This is not
supported by VSCode at present.
