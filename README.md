# desi-cli

A CLI tool to browse, stream, and download Indian movies & TV series (Bollywood, Marathi, Tamil, Telugu, Malayalam, Kannada, Bengali, Punjabi, and more).

Heavily inspired by [ani-cli](https://github.com/pystardust/ani-cli).

## Features

- Search & play Indian movies/series from the terminal
- Language filter (Hindi, Marathi, Tamil, Telugu, Malayalam, Kannada, Bengali, Punjabi)
- Multiple providers: YouTube (official channels) + Einthusan
- Movie & TV series support with episode selection
- Quality selection (best, 1080p, 720p, 480p, worst)
- Download videos
- History tracking with continue watching
- Self-update
- Multiple UI backends: fzf (default), rofi, dmenu
- Cross-platform: Linux, macOS, Windows, Android

## Dependencies

- curl, sed, grep
- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - Video source extraction
- [fzf](https://github.com/junegunn/fzf) - Interactive menu (optional; falls back to read)

### Player (choose one)
- mpv (recommended)
- VLC
- iina (macOS)

### Download (optional)
- aria2c
- ffmpeg

## Installation

### Linux / macOS
```bash
git clone https://github.com/arvndhl/desi-cli.git
cd desi-cli
sudo cp desi-cli /usr/local/bin/
```

### Windows (Git Bash)
```bash
git clone https://github.com/arvndhl/desi-cli.git
cd desi-cli
cp desi-cli /usr/bin/
```

### Android (Termux)
```bash
pkg install curl sed grep fzf yt-dlp mpv
git clone https://github.com/arvndhl/desi-cli.git
cp desi-cli/desi-cli $PREFIX/bin/
```

## Usage

```bash
desi-cli [options] [query]
```

### Options
| Flag | Description |
|------|-------------|
| `-h` | Show help |
| `-l <lang>` | Language filter: hindi, marathi, tamil, telugu, etc. |
| `-p <provider>` | Provider: youtube, einthusan, auto |
| `-q <quality>` | Quality: best, 1080p, 720p, 480p, worst |
| `-d` | Download instead of play |
| `-c` | Continue watching from history |
| `-D` | Delete history |
| `-e <num>` | Episode number (for series) |
| `-r <range>` | Episode range (e.g. 1-10) |
| `-v` | Use VLC player |
| `-s` | Use Syncplay |
| `-S <n>` | Select nth result directly |
| `-U` | Update script |
| `--rofi` | Use rofi menu |
| `--dmenu` | Use dmenu menu |
| `--no-detach` | Don't detach player |
| `--exit-after-play` | Exit after playing |
| `--debug` | Print debug info |

### Examples

```bash
# Search and play a movie
desi-cli sholay

# Search Marathi movie
desi-cli -l marathi duniyadari

# Search Tamil movie with Einthusan provider
desi-cli -p einthusan -l tamil

# Watch a TV series episode
desi-cli -l hindi -e 1 sacred games

# Download in 1080p
desi-cli -d -q 1080p RRR

# Continue from history
desi-cli -c
```

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `DESI_CLI_PLAYER` | (auto) | Video player (mpv/vlc/iina) |
| `DESI_CLI_QUALITY` | best | Default quality |
| `DESI_CLI_LANG` | all | Default language |
| `DESI_CLI_PROVIDER` | auto | Default provider |
| `DESI_CLI_DOWNLOAD_DIR` | . | Download directory |
| `DESI_CLI_HIST_DIR` | ~/.local/state/desi-cli | History directory |
| `DESI_CLI_NO_DETACH` | 0 | Don't detach player |
| `DESI_CLI_EXIT_AFTER_PLAY` | 0 | Exit after playing |
| `DESI_CLI_EXTERNAL_MENU` | 0 | External menu (0=fzf,1=rofi,2=dmenu) |
| `DESI_CLI_DEBUG` | 0 | Debug mode |

## Providers

### YouTube
Uses yt-dlp to search and extract videos from YouTube. Covers official channels like Rajshri, Shemaroo, Goldmines, Ultra Bollywood, etc.

### Einthusan
Searches Einthusan.tv (South Asian cinema archive) and uses yt-dlp for video extraction.

## License

GPL-3.0
