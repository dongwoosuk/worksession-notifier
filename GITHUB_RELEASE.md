# Worksession Notifier public beta

Get notified when references change. Refresh when you're ready.

Worksession Notifier watches your attached Worksession files and displays a popup when it detects a new saved version. Choose **Refresh references** to reload or **Later** to keep working. You do not need to open the Worksession panel to notice a change.

## Included

- Background file-change detection and a non-activating popup.
- Refresh references and Later actions.
- Combined notifications for multiple files.
- Commands to enable monitoring, inspect status, and reopen pending alerts.
- English installation guide with screenshots in Markdown and PDF.

## Compatibility

Windows and Rhino 8.35 or later in the Rhino 8 series, running .NET 8. Tested on Rhino 8.35. Other Rhino versions and macOS have not been validated.

## Install

Recommended: run **PackageManager** in Rhino, enable **Include pre-releases**, search for **worksession-notifier**, and install **0.2.2-beta.1**. Restart Rhino and run `WSNotifyStatus`.

Download the ZIP asset, extract it into a permanent folder, and drag `dist/WorksessionNotifier.rhp` into Rhino. Run `WSNotifyStatus`. Existing users should close Rhino before replacing the RHP and restart afterward.

The ZIP is the manual installation option. The YAK asset is the Windows package, also published on the Rhino Package Manager server.

## Validation

The installed YAK was tested in a dedicated Rhino 8.35 instance: automatic startup loading, changed-reference notification, Later without repeated alerts, reopening pending alerts, Refresh with geometry verification, a second saved change, and manual-refresh acknowledgement passed. Core tests passed 16 assertions. Yak uninstall and reinstall succeeded. This was an existing Windows user profile; clean-machine and live network/cloud collaboration tests remain unverified.

## Publisher and use

Published by **dongwoosuk**. Free for personal and commercial use under the included binary-use license. Source code is not published. See LICENSE.txt in the download or repository. Share the official release link rather than redistributing files.

## Known limitations

Alerts normally take 15–30 seconds after a stable local save and can take longer while Rhino is busy or files are syncing. Monitoring starts with a new baseline, so earlier changes are not reported. Timestamp and size checks do not identify geometry differences. Refresh applies to changed references throughout the Worksession, not only the displayed list.

Please report missed or repeated alerts with reproduction steps, Rhino version, storage type, and redacted `WSNotifyStatus` output.
