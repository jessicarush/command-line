# Customize bash command prompt

The default prompt is supposedly:

```bash
hostname:username current_directory$
```

Weirdly though, mine on mac os mojave is:

```bash
hostname:current_directory username$
```

To change it, you need to edit your `.bash_profile` file. It should be located directly in your home directory, You should see it when you:

```bash
cd ~/
ls -al
```

Add the following line to change the prompt to `username@hostname current_dir$ `:

```bash
export PS1="\u@\h \W$ "
```

Some common flags to work with:

`\d` – Current date  
`\t` – Current time  
`\h` – Host name  
`\#` – Command number  
`\u` – Username  
`\W` – Current working directory (ie: Desktop/)  
`\w` – Current working directory with full path (ie: /Users/Admin/Desktop/)  

You can also customize the colors for each section. The syntax is super cryptic so just see <https://www.howtogeek.com/307701/how-to-customize-and-colorize-your-bash-prompt/>.


## Zsh command prompt

Is almost the same but edit your `~/.zshrc` instead.

Example:

```bash
PS1="%n@%m %1~ %# "
```

In this string of variables:

- `%n` is the username
- `%m` is the HD name
- `%1~` is the current working directory path where the the number is how many levels you want to show and `~` strips the `$HOME` directory location.
- `%#` means that the prompt will show # if the shell is running with root (administrator) privileges, or else offers % if it doesn't.

Some other flags:

- `%D` – current date in yy-mm-dd  
- `%W` – current date in mm/dd/yy  
- `%T` – current time in 24 hour  
- `%t` – current time in 12 hour  

The zsh supports color and shades of gray to the prompt text such that it complements the background. You can pick a foreground (text) color between black, white, yellow, green, red, blue, cyan, and magenta.

To do this wrap `%F{color}%f` around the section to color, for example:

```bash
PS1="%F{cyan}%n%f@%m %1~ %# "
```

The above will make the username cyan. This next one will color all the parts:

```bash
PS1="%F{cyan}%n%f@%F{blue}%m%f %F{yellow}%1~%f %# "
```

## Default directory for new terminal sessions

Your `.bashrc` file is read when a new shell session starts up. Therefor, if you want to set a dfeault firectory: At the end of your `.bashrc`, you can simply `cd` to the directory you want to be the default.

```bash
# ...

# default directory for new terminal sessions
cd ~/Coding
```
