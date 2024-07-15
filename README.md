# Command Line Notes

## Table of Contents

<!-- toc -->

- [Common commands](#common-commands)
- [Special characters](#special-characters)
- [Environment Variables](#environment-variables)
- [Changing Shells](#changing-shells)
- [Search for processes and then kill them](#search-for-processes-and-then-kill-them)

<!-- tocstop -->

## Common commands

command | description
:------ | :----------
`--help` | type this after a command to see the help (try git push -u --help)
`alias wa="whatis"` | create keyboard shortcuts for common commands. Run `alias` alone to list all aliases. Note these are not persistent...use `.bashrc` or `.bash_aliases` for that. Note that if you are using variables in your alias, single quotes will resolve the variable when the alias is invoked (e.g. `alias p='$PATH'`) whereas double quotes will resolve the value when the alias is defined and keep that value (e.g. `alias p="$PATH"`).
`apropos` | find what man page is appropriate
`cal` | show a calendar
`cat` | output the entire contents of a file (e.g. `cat test.txt`). Note you can output multiple files (e.g. `cat test1.txt test2.txt`)
`cat -n` | print the contents with line numbers
`cd` | change directory
`cd -` | go to last directory
`cd ..` | go up one directory (two directories: cd ../..)
`cd ~` | go to home directory
`cd /` | go to the root directory
`chmod` | change file access permissions e.g. `chmod 755 README.py` (see [permissions.md](permissions.md))
`chown` | change the owner and group of a file or directory (e.g. `sudo chown -R jessica Files/` to change the owner or `sudo chown -R jessica:everyone Files/` to change both owner and group –note the `-R` is for recursive)
`clear` | clear the terminal display (or control L)
`cp` | copy a file or directory
`cp -r Notes Notes_copy` | duplicates the Notes directory and its contents as Notes_copy
`cp file1.txt backup/ `| creates a copy of file1 in a directory called backup
`cp file1.txt file2.txt` | copies file1 and creates file2
`date` | print out the current date
`diff` | compare difference between files
`diff -y` | to display diffs side by side
`diff -u` | to display diffs unified in one blob (similar to a git diff)
`dirs` | used with pushd and popd to see which directories are on the stack
`du -h` | disc usage... outputs sizes in the current directory
`du -h \| sort -hr \| head` | output the 10 largest files or directories in the current directory
`df -h` | displays free disk space
`echo` | print some arguments (e.g. `echo $PATH`)
`echo "USERNAME=ADMIN" > config.txt` | creates a new file if not exists with content `USERNAME=ADMIN`
`env` | look at your environment
`exit` | exit the shell
`export` | export/set a new environment variable
`find` | find files (see `man find`)
`find . -name 'README.md'` | find all files (recursively) in the current directory called `README.md`
`find . -type d -name 'venv'` | find all directories (recursively) in the current directory called `venv`
`find . -type d -name 'venv' -or -name 'node_modules'` | find all directories called `venv` or `node_modules`
`find . -name 'README.md' -not -path '*node_modules*'` | find and exclude paths with `-not -path`
`find . -type f -mtime -` | find files modified in the last 24hrs
`find . -type f -size +10M` | find files 10mb or greater. Units can be: k, M, G, T, P for kilobytes, megabytes, gigabytes, terabytes, petabytes
`grep` | find things inside files (e.g. `grep '<body>' index.html`)
`grep -r` | searches for files in directories that are within other directories (by default grep only searches the current directory, not sub directories)
`grep -i mountains` | search for mountains, case insensitive
`grep -r 'markdown-toc' .` | recursively search all files in the current directory for the term `markdown-toc`
`groups` | list all groups for the system
`gunzip` | decompress a file (`gunzip doc.pdf.gz`). Works the same as `gzip -d`
`gzip -k` | create a compressed copy of a file (e.g `gzip -k doc.pdf`)
`gzip -d` | decompress a file (`gzip -d doc.pdf.gz`). Works the same as `gunzip`
`head` | print out the first 10 lines of a given file
`head -n 5 app.log` | print out the first 5 lines of a file called `app.log`
`help` | will open a help file if it exists (for example: brew help, pip3 help)
`history <n>` | shows the previous (n=number) commands
`history \| grep 'venv'` | search history for anything with `venv` in it. Each command will have a number, enter `!num` to run that command
`hostname` | computers network name
`ifconfig` | show network interfaces (e.g. ip address)
`info` | reports information on a command (info python3, info dirs)
`ip address show` | the modern version of `ifconfig` shows ip addresses and ranges (linux only)
`ip link show` | shows network interfaces, such as wired connections and Wi-Fi adapters (linux only)
`jobs`, `bg`, `fg` | list currently running or suspended jobs, (e.g. if you suspend a process like `top` using `control z`, you can see it is stopped using the `jobs` command). Run `fg <n>` to resume the job using the number seen in the output of `jobs`, this will run it it the foreground... use `bg 1` to run the process in teh background.
`kill` | kill a process by ID (get ID with `ps` or `top`). Note the default signal is `-TERM` (software termination)
`kill -l` | list the signal types (some of these are also described in `man kill`), these types can be passed as an option by number, e.g. `kill -15` or by name (without the `SIG` part) e.g. `kill -TERM`
`kill -KILL <pid>` | force kill a process (`kill -9 <pid>` also works). You may need to use `sudo`
`killall` | kill a process by name (e.g. `killall -KILL node`)
`less` | interactive page through a file... similar to cat but more user friendly as it lets you arrow line by line or spacebar to page down (q to exit).
`ln` | by default creates a hard link (e.g. `ln original.txt hardlink.txt`)
`ln -s` | creates a soft link (e.g. `ln -s original.txt symlink.txt`)
`ls` | list current directory
`ls -alh` | lists everything in the current directory with details and human readable numbers
`lsb_release -a `| obtain information specific to your Linux distribution
`man` | read a manual page for a command (e.g. `man ls`), `q` to exit from the manual
`mdfind` | search for files or folders
`mdfind -name test -onlyin Documents` | searches for files or folders with the word 'test', in the directory called Documents
`mkdir` | make a directory
`mkdir "Python Books"` | use quotes to identify file names with spaces
`mkdir -p temp/stuff` | will create the temp and stuff directory directories, provided they don't already exist
`mkdir temp/stuff` | will only make the directory stuff if it can find the directory temp
`mv` | move (or rename) a file or directory
`mv Notes Stuff` | essentially renames the Notes directory as stuff (is actually creating a new dir)
`mv file.txt Notes `| moves file.txt into the Notes directory
`nano` | open a file in a very basic text editor
`open` | opens a file or directory (mac only)
`open .` | opens a finder window at the current directory (mac only)
`passwd` | allows you to change your password or another users password if you are admin (e.g. `sudo passwd guest`)
`popd` | pop directory (returns to the path at the top of the directory stack.)
`pushd` | push directory (saves the current working directory so it can be returned to at any time)
`ps` | show all terminal processes started by the current user
`ps -ax` | show all processes
`ps -ax \| grep 'Firefox'` | shoe all processes with 'Firefox'
`pwd` | print working directory
`rm` | remove - BE CAREFUL!
`rm -f` | force remove file without confirmation y/n
`rm -i` | remove with a confirmation
`rm -r` | remove a directory and its contents
`rm -rf` | force remove a directory (hidden files may prevent rmdir from working)
`rmdir` | remove an empty directory
`sed 's/dark/light/' file.txt` | replace the word "dark" with "light" in a file
`sort` | outputs sorted or merged lines of a text file
`sort -n` | outputs sorted or merged lines of a text file numerically
`sort -u` | outputs sorted and removes duplicates (unique values only)
`sort -u \| wc -l` | counts the number of unique lines
`su jessica` | switch user to username
`sudo` | super user do - only works if the current user has admin privileges - BE CAREFUL!
`sudo !!` | repeat the last command with sudo
`tail` | print out the last 10 lines of a given file
`tail -n 5 app.log` | print out the last 5 lines of a file called `app.log`
`tar -cf` | create a tar archive of multiple files (e.g. `tar -cf archive.tar file1.txt, file2.txt`). Note you can then use `gzip` to compress the archive to create a `archive.tar.gz`
`tar -czf` | create a compressed tar archive (same as if you used `gzip` after creating teh archive) e.g. `tar -czf archive.tar.gz file1.txt file2.txt`
`tar -xf` | extract files from a tar archive (e.g. `tar -xf archive.tar`). Note if the archive has also been compressed (with `tar -czf` or `gzip`), you don't need to decompress it first, `tar -xf` will handle it.
`tar -tf` | list filenames in a tar archive (e.g. `tar -tf archive.tar`)
`top` | much like activity monitor, displays live sorted information on processes (q to quit)
`top -o mem` | sort processes by memory instead of CPU usage
`touch` | makes a file if it does not exist (touch test.txt) or update the last modified timestamp of a file if it does exist
`uniq` | reads a file and outputs removing any duplicate *adjacent* lines. To remove all duplicates you would sort first (e.g. `sort file.txt \| uniq`). This command is similar to using the `-u` option with `sort` but provides more features like `-d` to only show duplicate lines and `-u` to only show unique lines or `-c` to show a count along with each line.
`wc` | output the number of lines, words, and bytes in a given file
`whatis` | gives a one line description of a command (whatis chown)
`which` | shows the path to where something lives (for example: which brew, which python3)
`who` | displays users currently logged in to the system
`whoami` | shows current username
`xargs` | take output of one command and use it as arguments for another command. This is similar to using `\|` but for commands that don't take that kind of input (e.g. `cat filesToDelete.txt \| xargs rm` or `find . -size +1M \| xargs ls -alh`). 


## Special characters 

character | description
:-------- | :----------
`>` | output result to a destination (e.g. `date > test.log`). Note this action will *replace* any existing content in the destination file if it exists or create a new file if it doesn't exist.
`>>` | output result to a destination (e.g. `date >> test.log`). Note this will *append* the output to an existing file or create a new file if it doesn't exist.
`\|` | takes the output of one command and passes as the input of another command (e.g. `ls -alh \| wc`)
`*` | represents any match, e.g. `echo *.md` will print out the names of all the markdown files in the current directory.
`?` | represents any single character match, e.g. `test?.md`
`{}` | will iterate through comma separated items (e.g. `echo test.{txt,js,css,html}` will output `test.txt test.js test.css test.html`)
`&` | put an ampersand at the end of a command to run it in the background. You can then check that it's running using `jobs` or bring it to the foreground using `fg <n>`.


## Environment Variables

To *temporarily* set an environment variable, use the `export` command in the command line:

```bash
export FLASK_APP=run.py
```

To *permanently* set an environment variable, place it in your `~/.bash_profile`.

```text
export FLASK_APP=run.py
```

To see all your current variables:

```bash
printenv
```

To see the value of a specific variable:

```bash
echo $FLASK_APP
```


## Changing Shells

To change the default shell to Bash:

```
chsh -s /bin/bash
```

To change the default shell to Zsh:

```
chsh -s /bin/zsh
```

To see a list of all included shells:

```
cat /etc/shells
```

## Search for processes and then kill them

```
ps -ax | grep 'search term' | awk '{print $1}' | xargs kill -9
```

You can also just run `ps` then when you find the process, note its PID and run:

```
sudo kill -9 <PID>
```

## Linux directories

dir | description
--- | -----------
/bin | essential user binaries
/boot | contains the linux kernel (boot files)
/dev | device files (for external devices like hard drives)
/etc | system config files
/home | home folders (user files)
/lib | essential kernel modules and shared libraries
/lost+found | recovered files
/media | removable media
/mnt | temporary mount points
/opt | option packages
/proc | kernel and process files
/root | root home directory
/run | application state files
/sbin | system binaries
/srv | service (server-related) data
/sys | virtual file system which allows modification of devices connected to the system
/tmp | temporary files (typically cleared on reboot)
/usr | user system resources (user binaries and read-only data)
/var | variable data files (log files)
