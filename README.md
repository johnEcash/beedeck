# beedeck

A custom [Elgato Stream Deck](https://www.elgato.com/stream-deck) plugin that connects to [MusicBee](https://www.getmusicbee.com/). It shows what's currently playing on your keys and dial, and lets you control MusicBee (love, shuffle/auto DJ, repeat, and dial navigation) through fully configurable hotkeys.

## Features

- **Now Playing key** — one action, configurable per button:
  - Artist, Title, Album, or Artist + Title
  - **Love** — filled/outline heart, sends a hotkey when pressed
  - **Album cover**
  - **Progress bar** — fills left to right as the track plays, with configurable font, colors, sizes, and outline
  - **Shuffle / Auto DJ** — one button reflecting MusicBee's single shuffle/auto-DJ toggle, with its own icon per state
  - **Repeat** — off / all / one, with its own icon per state
  - A neat "No music" state when nothing is playing
- **Album Cover dial**:
  - Shows the album cover on the touchscreen
  - Optional scrolling "Artist - Title" ticker next to the cover
  - Rotate left/right and press each send their own configurable hotkey
- All hotkeys are recorded by pressing them directly in the settings panel — no need to know virtual key codes
- File paths (`NowPlaying.txt` and the cover image) are configured once and shared by every button — nothing is hardcoded
- Icon colors (shuffle/auto DJ, repeat) are configurable per button

## Requirements

- Windows (hotkeys are sent via a background PowerShell process using the Windows `keybd_event` API, so this plugin does not work on macOS)
- [Stream Deck software](https://www.elgato.com/downloads) 7.1 or later
- MusicBee, configured to write now-playing info to a text file and a cover image (see [Configuration](#configuration))

## Installation (end users)

1. Download the latest `beedeck.streamDeckPlugin` file.
2. Double-click it. Stream Deck installs the plugin automatically.
3. Drag the **Now Playing** action onto one or more keys, and the **Album Cover** action onto a dial.
4. Open the settings of any button and set the paths to `NowPlaying.txt` and your cover image under **Files** (see [Configuration](#configuration)). This only needs to be done once — it applies to every button.
5. Configure the hotkeys you want each button to send (see below).

## Configuration

### NowPlaying.txt
https://github.com/johnEcash/mb_NowPlayingTags
MusicBee needs to be set up to write a small text file whenever the track or playback state changes, with one `key=value` pair per line. beedeck reads these keys (case-insensitive):

| Key | Example | Meaning |
|---|---|---|
| `artist` | `Queen` | Track artist |
| `title` | `The Show Must Go On` | Track title |
| `album` | `Innuendo` | Album name |
| `Love` | `1` | `1` = loved, `0`/empty = not loved |
| `duration` | `265` | Total track length in seconds (or `mm:ss`) |
| `position` | `42` | Current playback position in seconds (or `mm:ss`) |
| `shuffle` | `1` | `1` = shuffle is on |
| `autodj` | `1` | `1` = Auto DJ is on |
| `repeat` | `all` | `0`/empty = off, `all` = repeat playlist, `one` = repeat track |

`shuffle` and `autodj` are mutually exclusive in MusicBee's own UI (one button/hotkey cycles between normal → shuffle → auto DJ → normal), so beedeck reads them together to decide which of the three states to show.

### Album cover

MusicBee should also write the current album cover to an image file (`.jpg` or `.png`) whenever the track changes. In the settings panel, pick either file — beedeck automatically looks for the other extension at the same location if the chosen one isn't found, and falls back to a placeholder icon if neither exists.

### Hotkeys

Every hotkey field (Love, Shuffle/Auto DJ, Repeat, and the dial's rotate-left/rotate-right/press) is set the same way:

1. Open the button's settings in the Stream Deck software.
2. Click the hotkey field.
3. Press the key combination you want — it's recorded automatically, including Win/Ctrl/Shift/Alt.
4. Make sure the same shortcut is assigned to the matching action in MusicBee's own hotkey settings.

Since Shuffle/Auto DJ and Repeat are each a single toggle/cycle button in MusicBee, only one hotkey is needed per button — pressing it just tells MusicBee to advance to the next state, and beedeck reflects whatever state comes back in `NowPlaying.txt`.

> **Note:** Windows won't deliver a hotkey to an application that's running as administrator unless Stream Deck is also running as administrator. If a hotkey doesn't seem to reach MusicBee, check this first.

## Known limitations

- Windows only (see [Requirements](#requirements))
- The settings panels load a small UI component library from a CDN, so an internet connection is needed the first time you open a button's settings
- A hotkey won't reach an application running as administrator unless Stream Deck also runs as administrator




<img width="539" height="964" alt="afbeelding" src="https://github.com/user-attachments/assets/6b09f865-4bcc-4da2-9ca3-9dbc49515346" />
<img width="617" height="959" alt="afbeelding" src="https://github.com/user-attachments/assets/174334e8-3730-4d58-b0e6-208ccfb47a6a" />
<img width="571" height="1033" alt="afbeelding" src="https://github.com/user-attachments/assets/cc1763da-7877-4035-a756-5a16bc65e5ba" />


