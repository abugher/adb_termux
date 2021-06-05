# Description

The goal of this project is to expose the termux environment to an adb shell.


# Requirements

A rooted device is assumed.


# Scripts

`termux_user`

Become the user associated with the termux app.

`termux_shell`

Get a shell similar to the one in the termux app.


# Installation

These locations are recommended and assumed by the scripts:

`/sdcard/termux_user`

`/data/data/com.termux/files/home/bin/termux_shell`

That makes the `termux_user` script accessible by the adb shell user, and `termux_shell` accessible by the termux user (the user associated with the termux app, which will not be named "termux", unfortunately).


# Bugs

Group membership is broken.  In android, group membership is assigned when an app starts, and not when `su` is invoked.  The following have been observed to not work:

* networking - Permission is denied to open a socket.
* screen - Joining an existing screen session (`screen -dR sessionName`) doesn't work.  (I was hoping to get around the group problem this way.)  Ownership/permissions of `/dev/pts/*` may be part of the problem.  It may be possible to start a new screen session.


# Credit

[/data/data/com.termux/files/home/adb_like_termux.sh](This comment) is where I got most of the necessary actions to get a somewhat normal shell.

[https://github.com/termux/termux-app/issues/77#issuecomment-421474161](This follow-up comment) explains the group membership problem.
