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

