## Built-in keyboard shortcuts

## Customizing keyboard shortcuts

## Creating keybindings for R commands

There are 3 ways you can use extension functions to create keybindings that run R commands in the terminal:

1. `r.runCommand` to make a keybinding to run any R expression.
2. `r.runCommandWithEditorPath` to create a keybinding for an R expression where the placeholder value `$$` is interpolated with the current file path.
3. `runCommandWithSelectionOrWord` to create a keybinding for an R expression where `$$` is interpolated with the current selection or the current word the cursor is on.

Here are some example entries from `keybindings.json`:

```json
[
    {
        "description": "run drake::r_make()",
        "key": "ctrl+;",
        "command": "r.runCommand",
        "when": "editorTextFocus",
        "args": "drake::r_make()"
    },
    {
        "description": "load drake target at cursor",
        "key": "ctrl+shift+;",
        "command": "r.runCommandWithSelectionOrWord",
        "when": "editorTextFocus",
        "args": "drake::loadd($$)"
    },
    {
        "description": "knit to html",
        "key": "ctrl+i",
        "command": "r.runCommandWithEditorPath",
        "when": "editorTextFocus",
        "args": "rmarkdown::render(\"$$\", output_format = rmarkdown::html_document(), output_dir = \".\", clean = TRUE)"
    }
]
```
