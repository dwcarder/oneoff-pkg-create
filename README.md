oneoff-pkg-create
=================

Create a FreeBSD pkgng-style package from an arbitrary directory of files.

Based on [danrue/oneoff-pkg-create](https://github.com/danrue/oneoff-pkg-create)

Usage
=====

Provide a manifest_template with the name and particulars of your package, with the exception of the files to be installed which this script generates.

Optionally specify a directory that already contains a filesystem with the components to be packaged.

Otherwise, it will use `make` in the current directory assuming that the Makefile provides an 'install' target that allows specifying installation into a [STAGEDIR](https://wiki.freebsd.org/ports/StageDir) directory.

Usage: `build-pkg.sh -m <manifest_template> [-d <files_directory>]`

Example
=======

Create an example package that will install a file named /usr/local/test/README

    ./build-pkg.sh -m manifest_template.example -d example_root

The example package can be added with

    pkg add my-fortune-20140624.txz

Notes
=====

This script is largely based on the above prior work, though the specific syntax of the +MANIFEST file on my system (with version pkg-1.9.4_1a) differs from those previous examples and also doesn't match what is described in pkg-create(8).  That also differs slightly from what is found in the [pkg source code documentation](https://github.com/freebsd/pkg/blob/master/README.md).  Since the documentation is so poor and misleading, your best bet to find out how to structure a +MANIFEST file is to dump an existing package on your system.  

Ex: `pkg info -R <packagename>`
