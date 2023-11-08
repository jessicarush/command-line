# $PATH 

When you install a program, it often asks you to add a path to your $PATH (shell config file). After some time you may find your $PATH variable is a mess containing duplicate or triplicate paths. It is time to clean it up.

## Check you $PATH

The following command substitutes colons with new lines, sorts, counts the number of unique PATH occurrences, and displays:

```
echo $PATH | sed 's/:/\n/g' | sort | uniq -c
```

On macOS, the `$PATH` environment variable is constructed from various files and user-specific configurations. Here’s a breakdown:

1. **Global Paths:**
    - `/etc/paths`: This file contains a list of system-wide directories that are added to the `PATH` for all users. It typically includes directories like `/usr/local/bin`, `/usr/bin`, `/bin`, `/usr/sbin`, and `/sbin`.

2. **Shell-Specific Configuration Files:**
    - For `bash` (up to macOS Catalina by default): Global paths can be set in `/etc/profile` and `/etc/bashrc`.
    - For `zsh` (default from macOS Catalina onwards): Global paths can be set in `/etc/zshenv`, `/etc/zprofile`, `/etc/zshrc`, `/etc/zlogin`, and `/etc/zlogout`.

3. **User-Specific Configuration Files:**
    - For `bash` users: Paths can be set in `~/.bash_profile`, `~/.bash_login`, and `~/.profile` for login shells, and `~/.bashrc` for non-login shells.
    - For `zsh` users: Paths can be set in `~/.zshenv`, `~/.zprofile`, `~/.zshrc`, `~/.zlogin`, and `~/.zlogout`.

4. **Session-Specific Paths:**
    - These are paths set by session managers or parent processes that initiated the shell, like when using Terminal apps or IDEs that might modify the `PATH`.

5. **Launch Agents and Daemons:**
    - Paths set in plist files for launch agents (`~/Library/LaunchAgents`) and system-wide daemons (`/Library/LaunchDaemons` or `/System/Library/LaunchDaemons`) via the `EnvironmentVariables` key.

6. **Third-party Application Paths:**
    - Some applications install their own scripts or symlinks in directories like `/usr/local/share/` or `/usr/local/opt/`. These directories are often added to the `PATH` by the user's shell configuration files or by the application’s setup process.

When a new terminal session starts, these files are read in a specific order, which depends on the shell and whether the shell session is a login shell or an interactive/non-login shell. The paths from these sources are concatenated to form the `PATH` environment variable. If there are duplicates, the first occurrence in the `PATH` takes precedence.

Remember that when you change any of these files, you typically need to start a new shell session or source the file to apply the changes to your current session.