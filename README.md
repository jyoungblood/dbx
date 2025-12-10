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

### Add to your shell

Add an alias to your shell configuration file:

(add to `~/.zshrc` or `~/.bashrc` or `~/.bash_profile`):
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
dbx <project_name>
```

The script will:
1. Create a timestamped backup of your local database
2. Import the remote database to replace your local database

### Example

```bash
dbx oceancom
```

This will:
- Look for `config/oceancom.conf`
- Backup your local database to the configured backup directory
- Connect via SSH to the remote server
- Dump the remote database and import it locally

## Available Projects

To see all configured projects:
```bash
dbx
# (running without arguments shows available projects)
```
