# Creating a custom command

## Table of Contents

<!-- toc -->

- [bash_aliases](#bash_aliases)
- [A more complex example](#a-more-complex-example)

<!-- tocstop -->

## bash_aliases

There are a couple of different places were you can create aliases (command-line shortcuts). One is using the `.bash_aliases` file.

```bash
nano ~/.bash_aliases
```

Add your alias like so:

```text
alias sync-coding="rsync -r -a -v -e ssh --delete /Users/jessicarush/Documents/Coding jessica@rush-imac:/Users/jessica/Documents/
```

Reload the aliases in the command-line:

```bash
source ~/.bash_aliases
```

Run the command:

```bash
sync-coding
```

## A more complex example

In this example I want to run a command on every file in a directory. I'll start by running a test that will print out all the file names to the terminal.

The code structure looks like this:

```bash
for file in /dir/*
do
  cmd [option] "$file" >> results.txt
done
```

In the command line, separate clauses with a semicolon:

```bash
for i in *.md; do echo "hello $i"; done
```

This works so now I can try running my command:

```bash
for i in *.md; do markdown-toc -i $i; done
```

Now I can set this command up as my own custom command. This can be done in your `.bash_profile` or `.bashrc`. I think `.bash_profile` is more of a mac os thing and `.bashrc` is customary to linux. On my mac I also have a `bash_aliases` file and I can't remember if I created it or what but it makes sense to me do use it for this purpose. All will be located in your home directory:

```bash
cd ~/
ls -al
```

Normally an alias could be added to the file:

```bash
alias mytest="echo 'hello, testing'"
```

But when I try that using the `$i` variable, things break, so instead you can use a function:

```bash
# Markdown table of contents for all files in current directory:
mdtoc () {
  for i in *.md; do
    markdown-toc -i $i;
  done
}
```

Save, then refresh your file:

```bash
$ source ~/.bash_aliases
```
