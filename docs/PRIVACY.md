# MediaFlyouts Privacy Policy

**Effective date:** 9 October 2026
**Applies to:** MediaFlyouts / "Media Flyouts" for Windows, all distribution
channels (Microsoft Store, installer, portable ZIP, source build).

MediaFlyouts is a free, open-source desktop utility published by
ScleaverZer0ne. This policy explains what information the app handles and what
it does with it. The short version: **MediaFlyouts collects no personal data,
contains no telemetry, analytics or advertising, and sends nothing about you to
the developer.**

## 1. Data the app processes locally

To do its job MediaFlyouts reads information from your PC. All of this is
processed in memory on your device and is never transmitted anywhere.

| Information | Why it is read | Where it goes |
|---|---|---|
| Now-playing metadata (track title, artist, album, album art, playback state) from the Windows System Media Transport Controls | Media and Now Playing flyouts, taskbar widget | Memory only; discarded when the track changes or the app exits |
| Master and per-application volume, mute state, running audio app names and icons | Volume flyout and per-app mixer | Memory only |
| System audio output (WASAPI loopback) | Audio visualizer on the taskbar widget | Converted to a frequency spectrum in memory in real time; the audio is never recorded, stored or sent. Capture runs only while the visualizer is enabled and visible |
| Media and lock-key presses (`Play/Pause`, `Next`, `Previous`, `Stop`, `Volume Up/Down/Mute`, `Caps`, `Num`, `Scroll`, `Insert`) via a low-level keyboard hook | Triggering the flyouts | Only these specific keys are inspected. No other keystrokes are read, logged or stored. MediaFlyouts is not a keylogger |
| Peripheral device names, device type, battery level, charging state, Bluetooth address and connection state | Peripheral battery widget and flyouts | Memory only; custom names you assign are saved in settings (see §2) |
| Lock-key state, foreground fullscreen state, monitor layout, taskbar position, system theme and accent colour | Placing and styling the flyouts and widgets | Memory only |

## 2. Data the app stores on your device

- **Settings** — your preferences (enabled flyouts, positions, theme, custom
  peripheral names, app filter list, etc.) are saved in a local settings file in
  your user profile. "Open Config Folder" in the tray menu shows where. You can
  export, import or delete this file at any time; uninstalling the Store or
  installer version removes it.
- **Logs** — release builds write no log files. Developer (debug) builds may
  write a diagnostic log under the app's local data folder; it contains app
  events, never media content, audio or keystrokes.

Nothing is written outside your user profile and nothing is uploaded.

## 3. Network access

MediaFlyouts makes exactly one kind of network request, and only if you let it:

- **Update check** — when "check for updates" is enabled (or triggered manually
  from the dashboard), the app sends an HTTPS `GET` to
  `https://api.github.com/repos/scleaverzer0ne/MediaFlyouts-Releases/releases/latest`
  to compare version numbers. The request carries the user agent
  `MediaFlyouts` and the standard connection information any web request
  exposes (your IP address). It is handled by GitHub under the
  [GitHub Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement).
  MediaFlyouts sends no identifiers, settings or usage data with it.

Links in the tray menu or dashboard (Repository, Report a Bug, release page)
open in your default browser; those sites have their own policies.

Album art is obtained from the media player through Windows, not downloaded by
MediaFlyouts.

## 4. Data the developer receives

None. There is no account, sign-in, crash reporter, telemetry, analytics or
advertising SDK in the app. The developer cannot see who installs or uses
MediaFlyouts.

If you install from the **Microsoft Store**, Microsoft may collect install and
usage statistics under the
[Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement);
the developer only sees aggregated, anonymous Store statistics.

If you open an issue on GitHub, anything you post there is public and governed
by GitHub's policies.

## 5. Permissions

The Store package declares the `runFullTrust` capability. It is required for a
packaged desktop app to use the Windows APIs listed in §1 (keyboard hook, Core
Audio, WASAPI loopback, taskbar window placement, HID and Bluetooth battery
queries). It does not grant the app any network or cloud access beyond §3.

## 6. Children

MediaFlyouts is a general-purpose utility, is not directed at children, and
collects no data from anyone.

## 7. Changes to this policy

Changes are published in this file in the project repository and noted in the
changelog. The effective date at the top is updated with each change.

## 8. Contact

Questions about this policy: open an issue at
<https://github.com/scleaverzer0ne/MediaFlyouts-Releases/issues>.
