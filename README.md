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
--help | type this after a command to see the help (try git push -u --help)
alias wa="whatis" | create keyboard shortcuts for common commands
apropos | find what man page is appropriate
cat | print the whole file
cat test.txt | displays the file as one log blob (q to exit)
cd | change directory
cd - | go to last directory
cd ../ | go up one directory (two directories: cd ../../)
cd ~ | go to home directory
chmod | change file access permissions
chown | change the owner and group of a file
clear | clear the terminal display
cp | copy a file or directory
cp -r Notes Notes_copy | duplicates the Notes directory and its contents as Notes_copy
cp file1.txt backup/ | creates a copy of file1 in a directory called backup
cp file1.txt file2.txt | copies file1 and creates file2
dirs | used with pushd and popd to see which directories are on the stack
echo | print some arguments
env | look at your environment
exit | exit the shell
export | export/set a new environment variable
find | find files
grep | find things inside files
grep -R | searches for files in directories that are within other directories (by default grep only searches the current directory, not sub directories)
grep i mountains | searched for mountains, case insensitive
help | will open a help file if it exists (for example: brew help, pip3 help)
history n | shows the previous (n=number) commands
hostame | computers network name
info | reports information on a command (info python3, info dirs)
less | page through a file
less test.txt | displays the file in chunks (q to exit)
ls | list current directory
ls -al | lists everything in the current directory with details
lsb_release -a | obtain information specific to your Linux distribution
man | read a manual page
man ls | commands manual (q to exit from the manual)
mdfind | search for files or folders
mdfind -name test -onlyin Documents | searches for files or folders with the word 'test', in the directory called Documents
mkdir | make a directory
mkdir "Python Books" | use quotes to identify file names with spaces
mkdir -p temp/stuff | will create the temp and stuff directory directories, provided they don't already exist
mkdir temp/stuff | will only make the directory stuff if it can find the directory temp
mv | move (or rename) a file or directory
mv Notes Stuff | essentially renames the Notes directory as stuff (is actually creating a new dir)
mv file.txt Notes | moves file.txt into the Notes directory
open | opens a file or directory
open . | opens a finder window at the current directory
popd | pop directory (returns to the path at the top of the directory stack.)
pushd | push directory (saves the current working directory so it can be returned to at any time)
pwd | print working directory
rm | remove - BE CAREFUL!
rm -f | force remove file without confirmation
rm -i | remove with a confirmation
rm -r | remove a directory and its contents
rm -rf | force remove a directory (hidden files may prevent rmdir from working)
rmdir | remove an empty directory
su - jessica | switch user to username
sudo | super user root - BE CAREFUL!
touch | makes a file if it does not exist (touch test.txt)
whatis | gives a one line description of a command (whatis chown)
which | shows the path to where something lives (for example: which brew, which python3)
xargs | execute arguments - construct argument lists and and execute utility



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
