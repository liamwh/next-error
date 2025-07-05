# Next Error

Navigate to errors only (if you want), in 1 file or across multiple.

It's a fork of [yy0931/go-to-next-error](https://github.com/yy0931/go-to-next-error) that fixes few issues and strives for active maintenance.

![showcase](https://github.com/user-attachments/assets/fcae22db-4811-4c2a-a2cc-2477d7e621de)

## Commands

| Command                                    | ID                               |
| ------------------------------------------ | -------------------------------- |
| Next Problem (Error)                       | `next-error.next.error`          |
| Previous Problem (Error)                   | `next-error.prev.error`          |
| Next Problem in Files (Error)              | `next-error.nextInFiles.error`   |
| Previous Problem in Files (Error)          | `next-error.prevInFiles.error`   |
| Next Problem (Error, Warning)              | `next-error.next.warning`        |
| Previous Problem (Error, Warning)          | `next-error.prev.warning`        |
| Next Problem in Files (Error, Warning)     | `next-error.nextInFiles.warning` |
| Previous Problem in Files (Error, Warning) | `next-error.prevInFiles.warning` |

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
