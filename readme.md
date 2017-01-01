Server Backup Script
====================
This backup script creates an archive of incremental backups. Backup directories are named according to the current date, so the script is designed to be run on a daily basis.

The operation of the backup script is described here: [http://dev-notes.eu/2015/06/incremental-backup-on-server/](http://dev-notes.eu/2015/06/incremental-backup-on-server/).

## Usage Instructions
- Clone this repo to a suitable location, e.g. `~/sysadmin`
- Copy the `variables.sample` file to `variables`
- Edit `variables` with server specific data
- The script requires a backup user for MySQL - for sample commands see `backup-mysql-user`
- Create a symlink to `server-backup` within your `$PATH`
- Make sure `server-backup` is executable

The script works on the basis that you have created a non-sudo user with the name `${SERVERNAME}backup`, where `${SERVERNAME}` is the name of your server.

If necessary, the `setup` script sets up all necessary directories.

## Automated Setup
You can set up necessary backup and source directories by running `./setup` in this directory. This script creates all necessary symlinks and directories for the incremental backup to work.

## Setup Commands
Sample setup commands:
~~~
cd ~/sysadmin/server-backup

# Make the backup script (and setup script) executable
sudo chmod +x server-backup
sudo chmod +x setup

# Create a suitable symlink - to be run as root by a cronjob
sudo ln -s ~/sysadmin/server-backup/server-backup /usr/local/sbin/server-backup

# Run the setup script to set up necessary directory/symlink structure
sudo ./setup
~~~
