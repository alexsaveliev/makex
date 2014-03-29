# makex

**makex** is an experimental, incompatible `make` implementation written in Go.

Documentation: [makex on Sourcegraph](https://sourcegraph.com/github.com/sourcegraph/makex)

[![Build Status](https://travis-ci.org/sourcegraph/makex.png?branch=master)](https://travis-ci.org/sourcegraph/makex)
[![status](https://sourcegraph.com/api/repos/github.com/sourcegraph/makex/badges/status.png)](https://sourcegraph.com/github.com/sourcegraph/makex)
[![xrefs](https://sourcegraph.com/api/repos/github.com/sourcegraph/makex/badges/xrefs.png)](https://sourcegraph.com/github.com/sourcegraph/makex)
[![funcs](https://sourcegraph.com/api/repos/github.com/sourcegraph/makex/badges/funcs.png)](https://sourcegraph.com/github.com/sourcegraph/makex)
[![top func](https://sourcegraph.com/api/repos/github.com/sourcegraph/makex/badges/top-func.png)](https://sourcegraph.com/github.com/sourcegraph/makex)
[![library users](https://sourcegraph.com/api/repos/github.com/sourcegraph/makex/badges/library-users.png)](https://sourcegraph.com/github.com/sourcegraph/makex)

## Install

```
go get github.com/sourcegraph/makex/cmd/makex
makex -h
```

## Usage

Try running makex on the Makefiles in the `testdata/` directory.

```bash
$ cat testdata/sample0/y
cat: testdata/sample0/y: No such file or directory
$ makex -v -C testdata -f testdata/Makefile.sample0
makex: [sample0/y] mkdir -p sample0
makex: [sample0/y] echo hello bar > sample0/y
$ cat testdata/sample0/y
hello bar
$ makex -v -C testdata -f testdata/Makefile.sample0
$
```

```bash
$ ls testdata/sample1/
y1
$ makex -v -C testdata -f testdata/Makefile.sample1
makex: [sample1/y0] echo hello bar > sample1/y0
$ ls testdata/sample1/
y0  y1
$ makex -v -C testdata -f testdata/Makefile.sample1
$
```

## Known issues

makex is very incomplete.

* No support for setting or expanding variables (except for special-cased support for `$@` and `$^`)
* No support for filesystem globs except in the OS filesystem (not in VFSfilesystems).
* Many other issues.

