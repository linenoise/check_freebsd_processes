NAME
    check_freebsd_processess - Nagios plugin to monitor FreeBSD processes

DESCRIPTION
    This script acts as a plugin module for the Nagios IT infrastructure
    monitoring system. This script is designed to be run through NRPE on
    remote machines rather than being spawned by the central Nagios
    monitoring process. This pulls a process list through ps(1), and
    optionally matches the subset of those processes based on command name
    or execution state (wait, idle, swapped, etc).

    This has been tested with FreeBSD 7.2, but should work with any version
    of FreeBSD with compatible ps(1) output formatting.

  Available States

    *   disk-wait

        Marks a process in disk (or other short term, uninterruptible) wait.

    *   exit-wait

        The process is trying to exit.

    *   foreground

        The process is in the foreground process group of its control
        terminal.

    *   high-priority

        The process has raised CPU scheduling priority.

    *   idle

        Marks a process that is idle (sleeping for longer than about 20
        seconds).

    *   idle-int

        Marks an idle interrupt thread.

    *   in-trace

        The process is being traced or debugged.

    *   jailed

        Marks a process which is in jail(2).

    *   lock-wait

        Marks a process that is waiting to acquire a lock.

    *   locked

        The process has pages locked in core (for example, for raw I/O).

    *   low-priority

        The process has reduced CPU scheduling priority (see
        setpriority(2)).

    *   runnable

        The process is runnable.

    *   session-leader

        The process is a session leader.

    *   sleeping

        Marks a process that is sleeping for less than about 20 seconds.

    *   stopped

        The process is stopped.

    *   swapped-out

        The process is swapped out (aka "trashing" in the greater
        environment of high disk I/O).

    *   vfork-suspended

        The process is suspended during a vfork(2).

    *   zombie

        Marks a dead process (a 'zombie').

SYNOPSIS
  Command Line Interface
    Once you're in the libexec directory for your NRPE plugins (or libexec
    for nagios, in the case of monitoring the monitoring server), you can
    test the installation of this agent manually through the CLI. To poll a
    server to find out how many httpd (apache) processes are thrashing:

            ./check_freebsd_processes -w 1 -c 5 -p httpd -s swapped-out

    Poll a server to find out how many total processes are thrashing:

            ./check_freebsd_processes -w 15 -c 30

SEE ALSO
    If using an external configuration file, it should be structured
    according to the specification at
    <http://nagiosplugins.org/extra-opts/>.

    Thresholds given to this script should be in the format specified at
    <http://nagiosplug.sourceforge.net/developer-guidelines.html#THRESHOLDFO
    RMAT>.

    This module is built upon Nagios::Plugin by the Nagios Plugin
    Development Team. Further reading on Nagios, NPRE, and Nagios Plugins is
    available at <http://nagios.com/>.

AUTHOR
    This script is written and maintained by Dann Stayskal
    <dann@stayskal.com> and is available on his website, at
    <http://fragmentedzen.com/software/check_apache/>.

LICENSE
    Copyright (C) 2009 by Dann Stayskal.

    This program is free software; you can redistribute it and/or modify it
    under the terms of the GNU General Public License as published by the
    Free Software Foundation; either version 2 of the License, or (at your
    option) any later version.

    This program is distributed in the hope that it will be useful, but
    WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
    Public License for more details.

    You should have received a copy of the GNU General Public License along
    with this program; if not, write to the Free Software Foundation, Inc.,
    59 Temple Place, Suite 330, Boston, MA 02111-1307 USA

    Nagios, the Nagios logo, and Nagios graphics are the servicemarks,
    trademarks, or registered trademarks owned by Nagios Enterprises. All
    other servicemarks and trademarks are the property of their respective
    owner.

