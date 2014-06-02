==================
xterm-title-on-ssh
==================

description
===========

A little modofication of .bashrc script, that set tab title in gnome terminal as host that you are connecting to with ssh command.

usage
=====

You can replace whole .bashrc file in your home directory with this one, or you can make little modification of your .bashrc:
* find in your .bashrc string:
```bash
PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
```
* replace this string with new one:
```bash
PS1="${debian_chroot:+($debian_chroot)}\u@\h \w\a$$PS1"
```
* add to the end of the .bashrc new function:
```bash
ssh() {
        params=$*
        title=`echo $params | egrep -oi '[0-9a-z.]*\.[0-9a-z.]*'`
        echo -en "\033]0;$title\a"
        /usr/bin/ssh $params
}
```

