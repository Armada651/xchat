# X-Chat README

## X-Chat ("xchat") Copyright (c) 1998-2011 By Peter Zelezny.

This program is released under the GPL v2 with the additional exemption
that compiling, linking, and/or using OpenSSL is allowed. You may
provide binary packages linked to the OpenSSL libraries, provided that
all other requirements of the GPL are met. 
See file COPYING for details.

# What is it?

X-Chat is an IRC client for UNIX operating systems. I.R.C. is Internet
Relay Chat, see http://irchelp.org for more information about IRC in
general. Xchat runs on most BSD and POSIX compliant operating systems.

# The "azure_patches" Branch

X-Chat Aqua or XChat Azure requires some platform specific patches which
are not based on the work of XChat itself. However XChat Azure / Aqua uses
these customisations to meet platform specific needs. The `master` branch
of this repository will always contain XChats original, unmodified Code
synced from Subversion Repository at Sourceforge (https://sf.net/projects/xchat)

# Requirements:

* GTK+ 2.10 (this is available at http://www.gtk.org).

## X-Chat is known to work on, at least:

* Linux
* FreeBSD
* OpenBSD
* NetBSD
* Solaris
* AIX
* IRIX
* DEC/Compaq Tru64 UNIX
* HP-UX 10.20 and 11
* Mac OS X (note the X-Chat Aqua Frontend)
* Windows XP/2000/Vista/7

# Notes for packagers:

If you need your packages to work on i386, you don't need to compile with
--disable-mmx, because it's also checked at run-time.

# Python Scripts:

Scripts for 1.8.x are not compatible, and a brand new interface has be
written. Documentation can be found here: http://xchat.org/docs/.
Consider using the Python interface for your scripts, it's a very nice
API, allows for loading/unloading individual scripts, and gives you
almost all the features of the C-Plugin API.

# Perl Scripts:

Scripts for 1.8.x are compatible with the following exceptions:

* `IRC::command` will not interpret %C, %B, %U etc.
* `user_list` and `user_list_short`: If a user has both op and voice, only the op flag will be 1.
* `add_user_list`/`sub_user_list`/`clear_user_list`: These functions do nothing.
* `notify_list`: Not implemented. Always returns an empty list.
* `server_list`: Lists servers that are not connected aswell.
* Some print events may have new names and some were added.
* Text printed by scripts must now be UTF8.
* Text passed to scripts (via add_message_handler) will be encoded in UTF8.

# Autoloading Perl Scripts and Plugins

* X-Chat Azure automatically loads, at startup:
	* `~/.xchat2/*.pl` (`~/Library/Application Support/XChat Azure/*.pl` on a Mac with XChat Azure) Perl scripts
	* `~/.xchat2/*.py` (`~/Library/Application Support/XChat Azure/*.py` on a Mac with XChat Azure) Python scripts
	* `~/.xchat2/*.tcl` (`~/Library/Application Support/XChat Azure/*.tcl` on a Mac with XChat Azure) Python scripts
	* `~/Library/Application Support/XChat Azure/*.rb` on a Mac with XChat Azure for Ruby Scripts - not part of XChat Core (eg. this Repository)

# Control Codes:

    %%     -  A single percentage sign
    %C     -  Control-C (mIRC color code)
    %B     -  Bold Text
    %U     -  Underline Text
    %R     -  Reverse Text
    %O     -  Reset all Text attributes
    %XXX   -  ASCII XXX (where XXX is a decimal 3 digit number)
              (Eg: %007 sends a BEEP)

    %Cforeground,background will produce a color code, eg: %C03,10

These are now disabled by default (see Settings > Prefs > Input Box).
Instead you can insert the real codes via ctrl-k, ctrl-b and ctrl-o.
