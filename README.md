# Next Error

Makes error navigation seamless. It's a fork of [yy0931/go-to-next-error](https://github.com/yy0931/go-to-next-error) that fixes few issues and strives for active maintenance.
It adds the following commands to VSCode.

-   `Next Problem (Error)`
-   `Next Problem (Error, Warning)`
-   `Next Problem in Files (Error)`
-   `Next Problem in Files (Error, Warning)`
-   `Previous Problem (Error)`
-   `Previous Problem (Error, Warning)`
-   `Previous Problem in Files (Error)`
-   `Previous Problem in Files (Error, Warning)`

These commands are similar to the VSCode's built-in `Previous/Next Problem (Error, Warning, Info)` and `Next Problem in Files (Error, Warning, Info)`, but they select only markers of the specified severity.

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
-   We use hover instead of native markers to display diagnostics as this ensures proper cursor proximity navigation. This means there is a small delay for smooth scrolling setting but it also means that we can display errors with extensions like [Pretty TypeScript Errors](https://marketplace.visualstudio.com/items?itemName=yoavbls.pretty-ts-errors).
