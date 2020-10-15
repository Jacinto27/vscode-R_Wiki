The session watcher allows RStudio addins to be executed via an `{rstudioapi}` emulation layer.

The extension provides the command `r.launchAddinPicker` which opens a filterable list of installed addins that can be launched. Bind this to a key, or access it from the command palette as `R: Launch RStudio Addin`.

Alternatively, individual addin functions can be bound to keys using `r.runRCommand` as described in [Creating keybindings for R commands](https://github.com/Ikuyadeu/vscode-R/wiki/Keyboard-shortcuts#creating-keybindings-for-r-commands).

**Supported `{rstudioapi}` commands**

* `getActiveDocumentContext`
* `getSourceEditorContext`
* `isAvailable`
* `verifyAvailable`
* `insertText`
* `modifyRange`
* `readPreference`
* `readRStudioPreference`
* `hasFun`
* `findFun`
* `showDialog`
* `navigateToFile`
* `setSelectionRanges`
* `setCursorPosition`
* `setDocumentContents`
* `documentSave`
* `documentId`
* `documentPath`
* `documentSaveAll`
* `documentNew`
* `getActiveProject`
* `restartSession`
* `viewer`

**Verified compatible addin packages**

* `{reprex}`
* `{datapasta}`
* `{fnmate}`
* `{equisse}`
* `{remedy}`
* `{citr}`
* `{blogdown}`
* `{AlignAssign}`
* `{prefixer}`