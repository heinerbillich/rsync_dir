# rsyncdir

A rsync wrapper that continuously syncs a source directory to a target directory.
Used at the Swiss Light Source (http://www.psi.ch/sls) to copy experiment data.

The script as is requires a environmen variable  BEAMLINE_XNAME to be set. As a workaround do

```
$ BEAMLINE_XNAME=XXX ./rsyncdir -h
```


```
usage:
rsyncdir [options] source-dir  target-dir
rsyncdir [options]

rsyncdir will copy source-dir into target-dir repeatedly until
terminated with Ctrl-C.
rsyncdir uses rsync, hence only changes or new files are copied.
If source-dir and target-dir aren't specified rsyncdir will ask for the
values and suggest some defaults.

options
-l logfile    default: /Users/billich/rsyncdir-YYYY-MM-DD-<PID>.log. Use /dev/null to disable logging.
-d            debug, add debugging output: set -x
-q            quiet, little output to stdout
-r options    additional rsync options, just specify the single letter options, no leading dash "-"
-p nsec       pause at least nsec seconds between rsync calls, default is 180
-t nsec	      timeout and kill any rsync process which does run for more than 600 seconds.
        -h            print usage message and exit

        all other options are passed to rsync. Example
        $ rsyncdir --exclude=*.tmp Data10/. /media/mydisk

        Place target-dir in quotes if it contains white space. Example:
        $ rsyncdir some-dir  "/media/My Book"

        Put source-dir in quotes if you use wildcards. Example:
        $ rsyncdir "Data10/cat*" /media/mydisk
```


Contact: Heiner.Billich@psi.ch

