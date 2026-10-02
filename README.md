# beedeck

A Stream Deck plugin that controls and displays [MusicBee](https://www.getmusicbee.com/)

<img width="554" height="439" alt="afbeelding" src="https://github.com/user-attachments/assets/2db4834e-f0ce-4fd5-aede-c79f372811f7" />
<img width="511" height="429" alt="afbeelding" src="https://github.com/user-attachments/assets/0708b3f9-9464-4fd1-9bbc-382118305650" />


<img width="476" height="80" alt="afbeelding" src="https://github.com/user-attachments/assets/600c0895-f9a9-452f-a81c-2e7cea7167f2" />
<img width="484" height="79" alt="afbeelding" src="https://github.com/user-attachments/assets/8db8cd08-7aff-4f76-ba8d-4cf6ba1e47da" />
<img width="548" height="797" alt="afbeelding" src="https://github.com/user-attachments/assets/d3b53775-87bc-4e3a-a254-7b819509abb3" />






## Requirements

- [MusicBee](https://www.getmusicbee.com/) (tested on 3.6.x)
- An Elgato Stream Deck, Stream Deck Mini, or Stream Deck+
  - The **Now Playing** dial card (rating, repeat, shuffle, volume) requires a **Stream Deck+** specifically, since it uses its touch-strip dials. Everything else works on any Stream Deck.
- Stream Deck software 6.5 or newer
- Windows 10/11

## Installation

1. **MusicBee side:** copy `MB_beedeck.dll` into your MusicBee `Plugins` folder (usually `%AppData%\MusicBee\Plugins`), then restart MusicBee. A log file appears at `%AppData%\MusicBee\beedeck-plugin.log` if you need to troubleshoot a connection issue.
2. **Stream Deck side:** double-click the `com.jeroen.beedeck.streamDeckPlugin` file. The Stream Deck app installs it and adds a new **beedeck** category to the action list.
3. Make sure MusicBee is running before dragging a beedeck action onto a key — the plugin connects automatically and reconnects on its own if MusicBee restarts.

## Now Playing dial card (Stream Deck+)

Drag the **Now Playing** action onto all four dials. Together they form one continuous card, with a fixed role per dial:

| Dial | Rotate | Press |
|---|---|---|
| 1 | Previous / next track | Play / pause |
| 2 | Rating, in 0.5-star steps | Shows the next 3 tracks in the queue for 5 sec. |
| 3 | Repeat: off → all → one | Shuffle → Auto DJ → off |
| 4 | Volume | Toggle love |

The card also shows the cover, title (scrolls automatically if the name is too long), artist, album, elapsed/remaining time, a progress bar, rating stars, and a love heart. After 3 minutes with nothing playing, a quiet clock appears instead of the old info.

Configurable from the Property Inspector: 12 progress bar styles, full-size or smaller rounded album art, elapsed or remaining time shown.

## Now Playing (compact)

The same information — cover, title/artist, stars, heart, progress bar — on a single regular key, for a Stream Deck without dials. Press to play/pause. Same idle clock after 3 minutes of silence.

## All actions

**Now-playing info**
- **Now Playing** (Stream Deck+ dials) — the combined card described above
- **Now Playing (compact)** — the same info on a single key; press to play/pause
- **Artist** / **Title** / **Album** / **Artist + Title** — plain text keys
- **Cover** — just the album art
- **Next in queue** — shows the next track; press to skip to it
- **Progress** — progress bar key (elapsed, remaining, or a scrolling "Artist - Title" ticker)

**Playback control**
- **Love** — press to toggle
- **Rating** — shows the current star rating; press to rate up half a star, hold to rate down
- **Shuffle / Auto DJ** — press to cycle shuffle → Auto DJ → off
- **Repeat** — press to cycle off → all → one

**Sound settings**
- **Equalizer** — toggle on/off
- **Crossfade** — toggle on/off
- **Replay Gain** — press to cycle Off → Track → Album → Smart, with a small letter (T/A/S) showing the active mode

## Themes

One shared theme for every button at once — set it from the Property Inspector on any Now Playing button and it applies everywhere:

- **5 classic themes**: Amber Classic, Midnight Neon, Forest, Sunset Glow, Deep Ocean
- **5 standard Catppuccin flavors**: Latte (light), Latte (dark background), Frappé, Macchiato, Mocha
- **5 Catppuccin accent variants**: Rosewater, Flamingo, Peach, Teal, Lavender — each with a muted "Surface" background instead of black
- **10 well-known palettes**: Nord, Dracula, Gruvbox, Solarized, Tokyo Night, Rosé Pine, Everforest, Monokai, One Dark, Ayu
- **Custom** — every color, the font, and a background pattern set individually


