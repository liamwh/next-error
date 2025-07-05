# Next Error

Makes error navigation seamless. It's a fork of [yy0931/go-to-next-error](https://github.com/yy0931/go-to-next-error) that fixes few issues and strives for active maintenance.
It adds the following commands to VSCode.

-   `Next Problem (Error)`
-   `Go to Previous Problem (Error)`
-   `Next Problem in Files (Error)`
-   `Go to Previous Problem in Files (Error)`
-   `Next Problem (Error, Warning)`
-   `Go to Previous Problem (Error, Warning)`
-   `Next Problem in Files (Error, Warning)`
-   `Go to Previous Problem in Files (Error, Warning)`

These commands are like the VSCode's built-in `Go to Previous/Next Problem (Error, Warning, Info)` and `Next Problem in Files (Error, Warning, Info)`, but they select only markers of the specified severity.

---

To change the behavior of the F8 key from the default `Next Problem in Files (Error, Warning, Info)` to `Next Problem in Files (Error, Warning)`, add the following code to the `keybinding.json` (press `F1` or `Shift+Ctrl(Cmd)+P` then `Preferences: Open Keyboard Shortcuts (JSON)`).

```json
{
    "key": "f8",
    "command": "-editor.action.marker.nextInFiles",
    "when": "editorFocus"
},
{
    "key": "f8",
    "command": "next-error.nextInFiles.warning",
    "when": "editorFocus"
}
```

## Related GitHub Issue

https://github.com/microsoft/vscode/issues/105795.

## Known problems

-   If there are multiple errors in the exact same location, only the first one will be displayed.
-   Due to the limitations of the VSCode API, we use hovers to display diagnostics as this ensures proper cursor proximity navigation.
