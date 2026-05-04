# Todoist Text - Obsidian Plugin

This obsidian plugin integrates your Todoist tasks with markdown checkboxes in a text-centric approach.

Demo: ![demo](https://raw.githubusercontent.com/wesmoncrief/obsidian-todoist-text/master/demo.gif)

## Changes in this fork

The following changes were vibe coded for my personal use. It is not advised to clone this fork for your own use.

- Checking or unchecking a Todoist-backed checkbox now syncs the task state with Todoist automatically; no separate command is required.
- The "Todoist Text: Toggle todoist task" command remains available as a local checkbox toggle.
- New unchecked checklist items added inside a synced list create Todoist tasks automatically.
- Top-level bullets next to synced Todoist tasks also create new top-level Todoist tasks.
- New top-level tasks are created in the same section or project as the nearest same-level Todoist task when available.
- Indented checklist items are created as subtasks of the nearest parent Todoist task.
- New tasks are created with today's date by default.
- New task lines can include `-- p1` through `-- p4`; the suffix is converted to Todoist priority.
- Rendered Todoist tasks now link the task title directly and show priority outside the link, e.g. `[Task title](https://app.todoist.com/app/task/...) \(P1\)`.
- Todoist task links support both `todoist.com/showTask?id=...` and `app.todoist.com/app/task/...` URLs.
- The Todoist API client uses Obsidian `requestUrl`, handles Todoist API v1 task endpoints, and supports paginated filter results.

# Usage
1. Ensure you understand the security implications (see Security section of this file)
2. Install this plugin (Todoist Text) through Obsidian and enable it
3. Enter your Todoist API token in the plugin settings, as explained there
4. Read below sections to learn how to manipulate tasks

## Automatic creation of task list
Executing the command "Todoist Text: Replace keyword with todos" will search the currently open file and replace your keyword (configurable in the settings) with your todos from Todoist. The keyword will use your chosen [filter definition](https://todoist.com/help/articles/introduction-to-filters), which allows you to control exactly what tasks will be shown.

You can configure multiple keywords, each corresponding to a separate Todoist filter definition.

You can enable automatic replacement of the keyword with todos in the settings, so you won't have to manually run the "Todoist Text: Replace keyword with todos" command.

If you want to use a template file (e.g. for Daily Notes) and you have automatic replacement of your keyword enabled, you will find that your template file itself would have its keyword get replaced with todos. To prevent this, you can add your template folder to the "Excluded Folders" in the settings. Then, you can just place your keyword in the template file, and the files that it generates should automatically replace the keyword with your todos.

## Marking tasks as complete and re-opening
Checking or unchecking a Todo created by this plugin will update that task on Todoist.

You can still use the "Todoist Text: Toggle todoist task" command/hot key to toggle the current line locally. To do this, go to the Settings -> Hotkeys. Find the command "Todoist Text: Toggle todoist task", and set the hot key as desired. If you set the hot key to `<Cmd>-<Enter>`, be sure to remove `<Cmd>-<Enter>` from its default ("Toggle Checklist Status").

You can use the "Todoist Text: Toggle todoist task" command/hot key for any check list item, even if it is unrelated to Todoist. If the line contains a Todoist task URL, the checkbox change will update Todoist. If it does not contain a Todoist task URL, it will simply check/uncheck the line locally.

When closing a task, any indented subtasks in the local file will also be checked. When re-opening a subtask, parent tasks in the local file will also be unchecked.

## Adding/updating tasks
To add a task to Todoist from a synced list, add a new unchecked checklist item in the list. A top-level bullet item also works when it is next to existing Todoist tasks. Top-level tasks are created in the same section or project as the nearest same-level Todoist task when available; indented checklist items are created as subtasks of the nearest parent Todoist task.

New tasks are created with today's date by default. You can add a priority suffix like `-- p1` through `-- p4`; the suffix will be converted to Todoist priority and replaced with a linked task title after the task is created.

This plugin does not automatically update your local files based on remote changes to Todoist tasks. This may be supported later, please reach out via a GitHub issue if this would be useful to you.

## Security 
This plugin stores your Todoist API token in plain text in your .obsidian/plugins folder. Anyone with your Todoist API token could access and manipulate all of your Todoist data. Ensure that you are not syncing/sharing your .obsidian/plugins folder for security purposes. Use this plugin at your own risk.

## Feature requests
Please reach out (by filing a GitHub issue) if you'd like to discuss possible new features or need help with anything! If you do see a GitHub issue that already exists, feel free to comment on it, which could raise the priority/help inform how the feature is implemented.

See the [changelog](CHANGELOG.md) for recent changes.

I'm actively creating new features, so be sure to "watch" this repository (with the GitHub button near the top of the screen) to get notified so that you'll know when to update.

## Attribution
I copied the 'folder suggest' settings feature from https://github.com/liamcain/obsidian-periodic-notes - thanks!
