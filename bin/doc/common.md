COMMON OPTIONS
--------------

**-j JOBS**

Run no more than $(i,JOBS) commands simultaneously.

**--only-packages PACKAGES**

Ignore stanzas referring to a package that is not in $(b,PACKAGES).
$(b,PACKAGES) is a comma-separated list of package names.  Note that
this has the same effect as deleting the relevant stanzas from jbuild
files. It is mostly meant for releases.  During development, it is
likely that what you want instead is to build a particular
$(b,<package>.install) target.

**--debug-dependency-path**

In case of error, print the dependency path from the targets on the
command line to the rule that failed.

--debug-findlib
Debug the findlib sub-system.

--debug-backtraces
Always print exception backtraces.

--dev
Use stricter compilation flags by default.

--verbose
Same as $(b,--display verbose)

--display MODE
Control the display mode of Jbuilder.  See $(b,dune-config\(5\)) for
more details.

--no-buffer DIR
Do not buffer the output of commands executed by jbuilder. By default
jbuilder buffers the output of subcommands, in order to prevent
interleaving when multiple commands are executed in parallel. However,
this can be an issue when debugging long running tests. With
$(b,--no-buffer), commands have direct access to the terminal. Note
that as a result their output won't be captured in the log file. You
should use this option in conjunction with $(b,-j 1), to avoid
interleaving. Additionally you should use $(b,--verbose) as well, to
make sure that commands are printed before they are being executed.

--workspace FILE
Use this specific workspace file instead of looking it up.

--auto-promote
Automatically promote files. This is similar to running $(b,jbuilder
promote) after the build.

--force, -f
Force actions associated to aliases to be re-executed even if their
dependencies haven't changed.

--root DIR
Use this directory as workspace root instead of guessing it.  Note
that this option doesn't change the interpretation of targets given on
the command line. It is only intended for scripts.

--ignore-promoted-rules
Ignore rules with (mode promote)

--config-file FILE
Load this configuration file instead of the default one.

--no-config
Do not load the configuration file

-p, --for-release-of-packages
Shorthand for $(b,--root . --only-packages PACKAGE --promote ignore
--no-config). You must use this option in your $(i,<package>.opam)
files, in order to build only what's necessary when your project
contains multiple packages as well as getting reproducible builds.

-x
Cross-compile using this toolchain.

--diff-command CMD
Shell command to use to diff files