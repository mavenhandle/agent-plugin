---
name: mavenhandle-launch
description: Check a mobile app (iOS or Android) for App Store and Google Play rejection risks with MavenHandle, and see what to do next. Use when the user wants to know if their app will pass store review, asks for a pre-submission check, or mentions MavenHandle.
---

# Check an app with MavenHandle

MavenHandle scans a mobile app's source for App Store and Google Play rejection risks and
runs the rest of the launch on its website. This skill uses the `mavenhandle` MCP tools.
The first time a tool is used, the user signs in (or creates a free account) in their
browser and approves the connection.

## Steps

1. **Find the app.** Call `list_apps`. If the app is not there, ask the user for its name
   and call `add_app`.
2. **Make sure its source is connected.** A new app needs its code connected on the website
   (GitHub, or a zip upload). `add_app` and `get_app` return the link: give it to the user
   and wait until they say it is done. Never paste or upload source code through the tools.
3. **Scan.** Call `scan_app`. Each scan counts against the account's monthly scans, so do
   not start one the user did not ask for.
4. **Read the results.** Call `get_app` a few minutes later. Tell the user the verdict,
   the blockers first, and the one next step. Some findings may show only a title: the
   full detail is part of a paid report.
5. **Paid work happens on the website.** When a result includes a link for something paid
   (the full report, fixes, builds, store submission, more scans), show the user the link
   and the price exactly as given. Do not invent prices or links, and do not try to work
   around a locked result.

## When a tool refuses

Read the `message` and do what it says. A refusal with a `buy_on` link means the step is
paid: show the link. `not_found` means the app id is wrong: call `list_apps` again.
