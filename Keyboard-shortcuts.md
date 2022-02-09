## Suggested keyboard shortcuts

Add to `keybindings.json`:

```json
[
  {
    "key": "alt+-",
    "command": "type",
    "when": "editorLangId == r || editorLangId == rmd && editorTextFocus",
    "args": {"text": " <- "}
  },
  {
    "key": "ctrl+shift+m",
    "command": "type",
    "when": "editorLangId == r || editorLangId == rmd && editorTextFocus",
    "args": {"text": " %>% "}
  },
  {
    "key": "ctrl+shift+m",
    "command": "-workbench.actions.view.problems"
  },
  // RStudio keybinding for R Package development
  {
    "key": "ctrl+shift+b",
    "command": "r.build",
    "when": "resourceLangId == 'r'"
  },
  {
    "key": "ctrl+shift+e",
    "command": "r.check",
    "when": "resourceLangId == 'r'"
  },
  {
    "key": "ctrl+shift+t",
    "command": "r.test",
    "when": "resourceLangId == 'r'"
  },
  {
    "key": "ctrl+shift+d",
    "command": "r.document",
    "when": "resourceLangId == 'r'"
  },
  {
    "key": "ctrl+shift+l",
    "command": "r.loadAll",
    "when": "resourceLangId == 'r'"
  }
]

```

## Removed keyboard shortcuts

These keyboard shortcuts used to be set by this extension, but were removed
because they conflicted with default Visual Studio Code shortcuts. If you would
like to restore them, add these to `keybindings.json`:

```json
[
  {
    "command": "r.nrow",
    "key": "Ctrl+1",
    "when": "editorTextFocus && editorLangId == 'r'"
  },
  {
    "command": "r.length",
    "key": "Ctrl+2",
    "when": "editorTextFocus && editorLangId == 'r'"
  },
  {
    "command": "r.head",
    "key": "Ctrl+3",
    "when": "editorTextFocus && editorLangId == 'r'"
  },
  {
    "command": "r.thead",
    "key": "Ctrl+4",
    "when": "editorTextFocus && editorLangId == 'r'"
  },
  {
    "command": "r.names",
    "key": "Ctrl+5",
    "when": "editorTextFocus && editorLangId == 'r'"
  }
]
```

## Creating keybindings for R commands

There are 3 ways you can use extension functions to create keybindings that run
R commands in the terminal:

1. `r.runCommand` to make a keybinding to run any R expression.
2. `r.runCommandWithEditorPath` to create a keybinding for an R expression where
   the placeholder value `$$` is interpolated with the current file path.
3. `runCommandWithSelectionOrWord` to create a keybinding for an R expression
   where `$$` is interpolated with the current selection or the current word the
   cursor is on.

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
