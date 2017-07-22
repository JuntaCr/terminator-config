# Terminator Configuration
Makes the [terminator](http://www.tenshu.net/terminator/) look like Ubuntu gnome terminal.

Copy/merge config into ~/.config/terminator/config

The command prompt in terminator is not colorised by default, to fix this uncomment in ~/.bashrc:

```bash
force_color_prompt=yes
```

This also made the prompt show colors in an SSH session.


## Screenshots

![terminator_gnome](https://github.com/JuntaCr/terminator-config/raw/master/screenshots/terminator-gnome.png)


To snow git branch in command prompt update in ~/.bashrc:

```bash
# Add git branch if its present to PS1
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
if [ "$color_prompt" = yes ]; then
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
else
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi
unset color_prompt force_color_prompt
```
