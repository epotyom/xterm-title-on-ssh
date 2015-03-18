==================
xterm-title-on-ssh
==================

description
===========

A little modofication of .bashrc script, that set tab title in gnome terminal as host that you are connecting to with ssh or telnet command.

usage
=====

You can replace whole .bashrc file in your home directory with this one, or you can just add a few lines to the end of your .bashrc:
```bash
ssh() {
        params=$*
        title=`echo $params | egrep -oi '[0-9a-z.]*\.[0-9a-z.]*'`
        echo -en "\033]0;$title\a"
        /usr/bin/ssh $params
}
telnet() {
        params=$*
        title=`echo $params | egrep -oi '[0-9a-z.]*\.[0-9a-z.]*'`
        echo -en "\033]0;$title\a"
        /usr/bin/telnet $params
}
```

