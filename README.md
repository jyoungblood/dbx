# dbx

A simple database backup and sync utility that imports a remote database via SSH and saves a backup of the previous local version.

## Setup

### Installation

With degit:
```bash
npx degit jyoungblood/dbx ~/.dbx
```

Alternately, with clone with git:
```bash
git clone git@github.com:jyoungblood/dbx.git ~/.dbx
```

### Make the script executable

```bash
chmod +x ~/.dbx/dbx
```

### Add to shell

Add an alias to your shell configuration file *(in `~/.zshrc` or `~/.bashrc` or `~/.bash_profile`)*:
```bash
alias dbx="~/.dbx/dbx"
```


## Configuration

1. Copy the example configuration file:
```bash
cp config/example.conf config/myproject.conf
```

2. Edit `config/myproject.conf` with your project-specific settings:
   - SSH connection details (user, server, port, work path)
   - Remote database credentials (name, user, password)
   - Local database name
   - MySQL binary path, socket, and user
   - Backup directory path

## Usage

```bash
dbx myproject
```

This script will:
- Look for `config/myproject.conf`
- Backup your local database to the configured backup directory
- Connect via SSH to the remote server
- Dump the remote database and import it locally

## Available Projects

To see all configured projects:
```bash
dbx
# (running without arguments shows available projects)
```

---
### ** Security note **
This currently uses the mysqldump command's `-p` flag in the the remote database connection, using the password in the command line argument. While this is not ideal, it works. We're planning on changing this at some point, but in the mean time don't be alarmed when you see the standard "mysqldump: [Warning] Using a password on the command line interface can be insecure." warning. 