# log-archive

A simple, lightweight CLI tool to compress and archive log directories with automatic timestamp-based naming. Keeps your system clean while preserving logs in a compressed format for future reference.

## Features

- Compresses log directories into `.tar.gz` archives with timestamp filenames
- Shows file count, source size, archive size, and compression ratio
- Logs every archive operation to a history file
- Supports custom output directories and filename prefixes
- Color-coded terminal output with clear status indicators

## Requirements

- Bash (Unix/Linux/macOS)
- `tar` (pre-installed on most Unix systems)

## Installation

```bash
# Download the script
chmod +x log-archive

# Install system-wide (optional)
sudo mv log-archive /usr/local/bin/log-archive
```

## Usage

```bash
log-archive <log-directory> [options]
```

### Arguments

| Argument | Description |
|---|---|
| `<log-directory>` | Path to the directory containing logs to archive |

### Options

| Option | Description |
|---|---|
| `-o, --output <dir>` | Custom output directory (default: `~/.log-archives`) |
| `-p, --prefix <name>` | Custom prefix for the archive filename |
| `-l, --list` | List all previous archives |
| `-h, --help` | Show help message |

## Examples

```bash
# Archive system logs (saves to ~/.log-archives/)
log-archive /var/log

# Archive to a custom directory
log-archive /var/log --output /backup/logs

# Archive with a custom filename prefix
log-archive /var/log --prefix production
# → produces: production_20240816_100648.tar.gz

# View archive history
log-archive --list
```

## Archive Naming

Archives are named using the format:

```
<prefix>_YYYYMMDD_HHMMSS.tar.gz
```

For example:
```
logs_archive_20240816_100648.tar.gz
production_20240816_100648.tar.gz
```

## Archive History

Every archive operation is recorded to `~/.log-archives/archive_history.log` with:
- Date and time of the archive
- Path to the archive file
- Source directory
- Compressed file size

View the full history at any time with:

```bash
log-archive --list
```

## Default Output Location

Unless `--output` is specified, all archives are saved to:

```
~/.log-archives/
```

## License

MIT License — free to use, modify, and distribute.
