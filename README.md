# backup

A simple, portable shell script that creates timestamped backup copies of files.

```
$ backup myfile.txt
[INFO] Source: myfile.txt (1423 bytes)
[INFO] Backup: /home/user/myfile.txt.bck.2026-02-25-14-30-07
[ OK ] Backup created successfully: myfile.txt.bck.2026-02-25-14-30-07
```

## Install

Copy the script somewhere in your `$PATH`:

```bash
curl -fsSL https://raw.githubusercontent.com/dluc/backup/main/backup -o ~/.local/bin/backup
chmod +x ~/.local/bin/backup
```

Or clone and symlink:

```bash
git clone https://github.com/dluc/backup.git
ln -s "$(pwd)/backup/backup" ~/.local/bin/backup
```

## Usage

```
backup <filename>
```

The backup is created in the same directory as the original, named
`<filename>.bck.YYYY-MM-DD-HH-MM-SS`.

## Features

- Timestamped backups with second-level precision
- Colored output (auto-disabled on non-terminals; respects `NO_COLOR`)
- Clear error messages with suggested fixes
- Handles filenames with spaces, dashes, globs, quotes, unicode, etc.
- Compatible with bash 3+, zsh, WSL, macOS, Linux

## Validation

The script validates the input and reports actionable errors for:

- Missing or extra arguments
- File not found
- Directories, symlinks, devices, sockets, pipes
- Permission issues (read on source, write on target directory)
- Disk full / copy failures
- Backup name collisions

## License

MIT
