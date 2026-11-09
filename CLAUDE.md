# claude-git

A Claude Code mod, a fork of [manuel-will/cc-source-control](https://github.com/manuel-will/cc-source-control). The plugin `git` lives in `source-control/`. The README describes what it does.

## Checks

Run these after each change:

```
claude plugin validate ./source-control
claude plugin test ./source-control
```

## Test in a live session

The tests do not show the layout. After a change to what the mod draws, test it in a live session:

1. Open a new terminal that runs Claude Code with the mod loaded from the `source-control` folder of the repo you work in:

   ```
   claude --plugin-dir <path to the source-control folder>
   ```

   This loads the files as they are in that folder, also changes that are not committed.

2. Tell the user that the terminal is open, and what to look at.

## Release

Claude Code runs the copy of the mod that it made at install time, not this folder. It updates that copy only when the `version` in `source-control/.claude-plugin/plugin.json` changes, not on each commit.

1. When a change touches the shipped files (`source-control/hooks`, `source-control/types`, `source-control/.claude-plugin`), raise `version` in `source-control/.claude-plugin/plugin.json`.
2. Push to `main`.
3. Update the local installation:

   ```
   claude plugin marketplace update zirkelc
   claude plugin update git@zirkelc
   ```

4. Tell the user to run `/reload-plugins`, so the running sessions load the new version.
