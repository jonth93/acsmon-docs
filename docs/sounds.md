# Sounds & Audio Cues

Audible feedback for in-app notifications, alerts and live dashboard updates

ACS Monitor can play a sound when something happens — an in-app notification arrives, an alert escalates, or a dashboard widget detects a status change. Every sound is configurable from **Settings &rarr; Sounds**, and the bell in the top bar can be muted independently from the rest.

### Settings &rarr; Sounds tab

A table with one row per notification type. Each row picks the sound that plays for that type, with a Test button next to it so you can audition without saving. Choices save the moment you change them — no separate "Save" button.

| Notification type | Plays when… |
| --- | --- |
| In-app bell notification | A new notification appears in the bell at the top of the page. |
| Critical alert | An alert event with critical severity fires (reserved for future broadcast hookup). |
| Warning alert | An alert event with warning severity fires (reserved for future broadcast hookup). |
| Info alert | An informational alert fires (reserved for future broadcast hookup). |
| Toast / inline message | A short toast appears on screen (reserved for future expansion). |

### Built-in sound library

20 original tones are bundled with the app, generated from first principles so they carry no licensing constraints. They cover the full range of operations contexts:

Subtle / info

Soft single chime, ascending two-tone ding, marimba-style mac chime.

Notifications

Slack-style ping, bright bell, classic landline ring, doorbell ding-dong.

Warnings

Three medium beeps, descending two-tone, bright pager-style 2.7 kHz triple-beep.

Critical / klaxons

Siren sweep, urgent triple-pulse, industrial buzzer, naval klaxon, submarine AHOOGA, air-raid siren, modern car-alarm.

UI / misc

Confirm click, low cardiac heartbeat (good for "still alive" pings), retro beep-boop.

### Custom uploads

Upload your own **WAV** or **MP3** files (max 1 MB each) from the Custom Sounds card on the Sounds tab. Uploads appear in every dropdown alongside the built-ins. If you delete a custom sound that's currently in use, the affected notification type automatically reverts to its default — nothing breaks.

### Notification bell

When a new in-app notification arrives, the bell plays the sound you've picked under **In-app bell notification**. A speaker icon next to *Mark all read* in the bell dropdown lets you mute or unmute — your choice is remembered across reloads. Sound is silent on initial page load and only fires when the unread count actually rises, so opening a page that already has unread items doesn't blast at you.

### Per-widget audio cues

Seven dashboard widget types can play their own sound when their data changes. Widgets often see live updates faster than the alert pipeline can deliver them, so this gives you an audible heads-up the moment a dashboard updates — useful for wall-mounted NOC displays.

Open any of these widgets in the Add or Edit panel and flip on **Play sound on update**. Pick a specific sound or leave it on *Use global default* to inherit the sound from Settings &rarr; Sounds:

| Widget | Plays when… |
| --- | --- |
| Alert Summary | The critical count rises. |
| Alert List | A brand-new alert appears at the top. |
| Device Health | Any device or monitor flips into down / warning / critical / degraded. |
| Status Card | Any tracked entity flips into a bad state. |
| Status Grid | Any grid cell flips into a bad state. |
| Monitor List | Any monitor flips into down, degraded or warning. |
| Uptime Timeline | The most-recent segment flips off "up". |

### Browser autoplay policies

Modern browsers block sound from playing until the user has interacted with the page (clicked, pressed a key, etc.). ACS Monitor handles this gracefully — if a notification arrives before that first interaction, the sound is silently dropped instead of erroring, and audio resumes from the very next event after any click. You'll never see a sound-related popup or permission prompt.
