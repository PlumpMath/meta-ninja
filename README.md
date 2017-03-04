Ninja Meta-Build system
=======================

This script configures a `build.ninja` file by scanning a target folder for
files with the correct extension. It is completely written in GNU Guile Scheme.

The script expects a `project.scm` file to be present in the folder from which
meta-ninja is being run. Here's an example:

```scheme
(settings
  ; use the Gnu C++ compiler
  (compiler  "g++")
  ; put object files in the `build` directory
  (build_dir "build")
  ; run `pkg-config` on these, to get $cflags and $ldflags
  (libraries ("ncurses" "guile-2.0"))
  ; search for *.cc
  (extension "cc")
  ; run with these extra $cflags
  (cflags    "-O3 -Wall"))

(target
  ; name of the target
  (name      "slasher")
  ; type: executable, shared-object or archive
  (type      executable)
  ; source folder
  (sources   ("src")))
```

