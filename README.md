# Command Line Notes

## Table of Contents

<!-- toc -->

- [Common commands](#common-commands)
- [Environment Variables](#environment-variables)
- [Changing Shells](#changing-shells)

<!-- tocstop -->

## Common commands

command | description
------- | -----------
`--help` | type this after a command to see the help (try git push -u --help)
`alias wa="whatis"` | create keyboard shortcuts for common commands
`apropos` | find what man page is appropriate
`cat` | output the entire contents of a file (e.g. `cat test.txt`). Note you can output multiple files (e.g. `cat test1.txt test2.txt`)
`cat -n` | print the contents with line numbers
`cd` | change directory
`cd -` | go to last directory
`cd ..` | go up one directory (two directories: cd ../..)
`cd ~` | go to home directory
`cd /` | go to the root directory
`chmod` | change file access permissions
`chown` | change the owner and group of a file
`clear` | clear the terminal display (or control L)
`cp` | copy a file or directory
`cp -r Notes Notes_copy` | duplicates the Notes directory and its contents as Notes_copy
`cp file1.txt backup/ `| creates a copy of file1 in a directory called backup
`cp file1.txt file2.txt` | copies file1 and creates file2
`date` | print out the current date
`dirs` | used with pushd and popd to see which directories are on the stack
`echo` | print some arguments (e.g. `echo $PATH`)
`echo "USERNAME=ADMIN" > config.txt` | creates a new file if not exists with content `USERNAME=ADMIN`
`env` | look at your environment
`exit` | exit the shell
`export` | export/set a new environment variable
`find` | find files
`grep` | find things inside files
`grep -R` | searches for files in directories that are within other directories (by default grep only searches the current directory, not sub directories)
`grep -i mountains` | search for mountains, case insensitive
`head` | print out the first 10 lines of a given file
`head -n 5 app.log` | print out the first 5 lines of a file called `app.log`
`help` | will open a help file if it exists (for example: brew help, pip3 help)
`history <n>` | shows the previous (n=number) commands
`hostname` | computers network name
`ifconfig` | show network interfaces (e.g. ip address)
`info` | reports information on a command (info python3, info dirs)
`ip address show` | the modern version of `ifconfig` shows ip addresses and ranges (linux only)
`ip link show` | shows network interfaces, such as wired connections and Wi-Fi adapters (linux only)
`less` | interactive page through a file... similar to cat but more user friendly as it lets you arrow line by line or `spacebar` to page down (q to exit).
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
`open` | opens a file or directory (mac only)
`open .` | opens a finder window at the current directory (mac only)
`popd` | pop directory (returns to the path at the top of the directory stack.)
`pushd` | push directory (saves the current working directory so it can be returned to at any time)
`pwd` | print working directory
`rm` | remove - BE CAREFUL!
`rm -f` | force remove file without confirmation y/n
`rm -i` | remove with a confirmation
`rm -r` | remove a directory and its contents
`rm -rf` | force remove a directory (hidden files may prevent rmdir from working)
`rmdir` | remove an empty directory
`sort` | outputs sorted or merged lines of a text file
`sort -n` | outputs sorted or merged lines of a text file numerically
`sort -u` | outputs sorted and removes duplicates (unique values only)
`sort -u | wc -l` | counts the number of unique lines
`su jessica` | switch user to username
`sudo` | super user root - BE CAREFUL!
`sudo !!` | repeat the last command with sudo
`tail` | print out the last 10 lines of a given file
`tail -n 5 app.log` | print out the last 5 lines of a file called `app.log`
`touch` | makes a file if it does not exist (touch test.txt) or update the last modified timestamp of a file if it does exist
`uniq` | reads a file and outputs removing any duplicate *adjacent* lines. To remove all duplicates you would sort first (e.g. `sort file.txt | uniq`). This command is similar to using the `-u` option with `sort` but provides more features like `-d` to only show duplicate lines and `-u` to only show unique lines.
`wc` | output the number of lines, words, and bytes in a given file
`whatis` | gives a one line description of a command (whatis chown)
`which` | shows the path to where something lives (for example: which brew, which python3)
`whoami` | shows current username
`xargs` | execute arguments - construct argument lists and and execute utility


## Special characters 

character | description
--------- | -----------
`>` | output result to a destination (e.g. `date > test.log`). Note this action will *replace* any existing content in the destination file if it exists or create a new file if it doesn't exist.
`>>` | output result to a destination (e.g. `date >> test.log`). Note this will *append* the output to an existing file or create a new file if it doesn't exist.
`|` | takes the output of one command and passes as the input of another command (e.g. `ls -alh | wc`)

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
