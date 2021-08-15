# Command Line Tricks


Command line tricks noted.

<!--more-->

## Passing arguments to a command from a text file

Using:
- `sed`
- `xargs`

For example, to install two lists of packages in Ubuntu:

```bash
cat list1.txt list2.txt | sed 's/#.*$//' | xargs sudo apt install
```

- `xargs` takes the output from `sed` as arguments to `apt`
- `sed 's/#.*$//'` filters out those lines after `#`. So the `list2.txt` can have comments like the following
```txt
# Comment

item1
item2  # A comment after an item
    item3  # indent supported
```

## Passing multiple lines of string

Using heredoc to pass the string between two delimiters (e.g. `EOF`)

```bash
cat << "EOF" >> ~/.xprofile
# ~/.xprofile
export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
ibus-daemon -drx
EOF
```

Will append the following lines in `~/.xprofile`:

```bash
# ~/.xprofile
export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
ibus-daemon -drx
```

## progress

[`progress`](https://github.com/Xfennec/progress) measures the speed and progress of ongoing commands.

After installation, just [launch](https://github.com/Xfennec/progress#what-can-i-do-with-it) `progress` in the terminal.

## pv

[`pv`](https://linux.die.net/man/1/pv) shows transfer speed and /or progress through a Unix pipe. `pv` works like `cat`. For example,

```bash
cat file > other_file # no output with cat
pv file > other_file  # With progress
```

```bash
# Showing both compression progress and speed
pv file | gzip > file.gz

# Sandwich form, showing speed without progress
cat file | pv | gzip > file.gz
```

