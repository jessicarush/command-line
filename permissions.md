# Permissions

Through the command line, you can view the permissions of each file and folder in your current directory:

```bash
ls -al
```

The permissions are represented as a 10 position binary string. Each position indicates a yes or no for a particular thing. For example, consider this string indicates that this is a file, not a directory, the current user can read and write but all other users and groups can only read the file: `-rw-r--r--`

```
position    values      description

1.          d or -      indicates if the item is a directory (d) or not (-)
2.          r or -      current user's read  permissions
3.          w or -      current user's write permissions
4.          x or -      current user's executable permissions
5.          r or -      group's read  permissions
6.          w or -      group's write permissions
7.          x or -      group's executable permissions
8.          r or -      everyone else's read  permissions
9.          w or -      everyone else's write permissions
10.         x or -      everyone else's executable permissions
```

So, a file that has read-only permissions for everyone would look like this: `-r--r--r--` whereas a directory that everyone has access to read but only the current user can modify would look like this: `drwxr-xr-x`. Directories are always marked as executable by default, otherwise you wouldn't be able to open them.

## Changing permissions with chmod

We can change permissions for any file or directory using the following pattern:

```bash
sudo chmod <permission code> filename.py
```

For the permission code, we need to provide a binary answer for each of the 9 positions after the first one (indicates if it's directory). Rather than typing in 9 binary numbers, we instead use a 3-digit octal number where the first digit maps to the current user's permissions, the second digit maps to the group's permissions and the third maps to everyone else's permissions.

If we start by looking at just one of these user subsets, we have three positions to provide values for: read, write, executable. In binary (radix=2), three positions from left to right `111` would be equivalent to (1 x 2<sup>2</sup>) + (1 x 2<sup>1</sup>) + (1 x 2<sup>0</sup>) or `4 + 2 + 1`. As a result, we can add these together to provide 1 octal number that is able to represent every combination of these binaries. For example:

```
permission      binary      conversion      octal

---             000         0 + 0 + 0       0
r--             100         4 + 0 + 0       4
rw-             110         4 + 2 + 0       6
r-e             101         4 + 0 + 1       5
rwe             111         4 + 2 + 1       7
-w-             010         0 + 2 + 0       2
-we             011         0 + 2 + 1       3
--e             001         0 + 0 + 1       1
```

Now we just put these three octal numbers together to define the permissions for each of the three user groups. For example:

```
permissions     octal code

-r--r--r--      444
-rwer--r--      744
-rw-rw-rw-      666
-rwer-er-e      755
```
