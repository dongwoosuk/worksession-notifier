# Worksession Notifier

**Get notified when references change. Refresh when you're ready.**

Worksession Notifier monitors files attached to a Rhino Worksession and shows a popup when a saved change is detected. Keep the Worksession panel closed and choose when to reload your references.

![Worksession update notification](docs/images/popup-single.png)

## Choose when to refresh

- **Refresh references** reloads changed references through Rhino's Worksession Refresh command.
- **Later** dismisses the alert and lets you keep working with the current reference geometry.
- **WSNotifyShow** brings pending notifications back when you are ready.

The popup does not activate itself or automatically refresh your model. Multiple changed files appear together in a scrolling list. The same saved version does not repeatedly notify you after dismissal; another saved change can trigger a new alert.

## Requirements

Windows, Rhino 8.35 or later in the Rhino 8 series, running **.NET 8**. Rhino 8.35 is the tested version; later service releases still require verification. Rhino 7, Rhino 9, and macOS are not validated for this release.

## Install

In Rhino, run **PackageManager**, enable **Include pre-releases**, search for **worksession-notifier**, and install **0.2.2-beta.1**. Restart Rhino and run `WSNotifyStatus`.

You can also download the public beta from [GitHub Releases](https://github.com/dongwoosuk/worksession-notifier/releases).

For a manual install, download the release ZIP, extract it to a permanent folder, and drag `dist/WorksessionNotifier.rhp` into Rhino. Run `WSNotifyStatus` to confirm monitoring is enabled. Keep the extracted folder in place: Rhino registers the RHP at that location. Restart Rhino after updating.

See the [illustrated installation guide](Installation_Guide_and_Commands_EN.md) or [PDF guide](Installation_Guide_and_Commands_EN.pdf).

## Commands

| Command | Action |
|---|---|
| `WSNotifyStatus` | Show monitoring state, watched files, pending changes, and access errors. |
| `WSNotifyOn` | Enable monitoring and establish a new baseline. |
| `WSNotifyOff` | Disable monitoring and clear pending notifications. |
| `WSNotifyShow` | Reopen pending notifications dismissed with Later or the close button. |

## What to expect

File timestamps and sizes are checked approximately every 15 seconds on a background worker. Stable observations normally produce an alert 15–30 seconds after a saved change becomes visible locally. Network delays and active Rhino commands can increase this interval.

Changes made before monitoring starts are not reported. Cloud changes are detected after local synchronization. This detects saved-file changes, not geometry differences; changes preserving both timestamp and size can be missed. Missing or inaccessible files are reported by `WSNotifyStatus`.

**Refresh references applies Rhino's Worksession Refresh operation across the current Worksession; it is not limited to the files listed in the popup.** Later leaves the loaded geometry unchanged. The stability check cannot guarantee that another program has finished writing a file.

## Feedback

Report problems through [GitHub Issues](https://github.com/dongwoosuk/worksession-notifier/issues). Include Rhino version, Windows version, plugin version, storage type (local/network/cloud), reproduction steps, and relevant `WSNotifyStatus` output. Remove private paths and project names before posting.

## Publisher and license

Published by **dongwoosuk**. Free to use for personal and commercial work. Source code is not published. See [LICENSE.txt](LICENSE.txt) for the binary-use terms. Share the official download link rather than redistributing the files.
